# labpy8

    import json

    class DaftarNilai:
    def __init__ (self):
        self.data = {}
        self.load_data()

    def load_data(self):
        try:
            with open('data_nilai.json', 'r') as file:
                self.data = json.load(file)
        except FileNotFoundError:
            self.data = {}
        except json.JSONDecodeError:
            print("File data_nilai.json rusak, memulai dengan data kosong.")
            self.data = {}

    def save_data(self):
        with open('data_nilai.json', 'w') as file:
            json.dump(self.data, file)

    def tambah(self):
        nama = input("Masukkan nama mahasiswa: ")
        if nama in self.data:
            print("Nama mahasiswa sudah ada. Silakan gunakan opsi ubah untuk memperbarui nilai.")
            return
        try:
            nilai = int(input("Masukkan nilai mahasiswa: "))
            self.data[nama] = nilai
            self.save_data()
            print("Data berhasil ditambahkan!")
        except ValueError:
            print("Nilai harus berupa angka.")

    def tampilkan(self):
        if not self.data:
            print("Data masih kosong.")
        else:
            print("Daftar nilai mahasiswa:")
            for nama, nilai in sorted(self.data.items()):
                print(f"{nama}: {nilai}")

    def hapus(self, nama):
        if nama in self.data:
            del self.data[nama]
            self.save_data()
            print("Data berhasil dihapus!")
        else:
            print("Nama mahasiswa tidak ditemukan.")

    def ubah(self, nama):
        if nama in self.data:
            try:
                nilai_baru = int(input("Masukkan nilai baru: "))
                self.data[nama] = nilai_baru
                self.save_data()
                print("Data berhasil diubah!")
            except ValueError:
                print("Nilai harus berupa angka.")
        else:
            print("Nama mahasiswa tidak ditemukan.")

    def cari(self, nama):
        if nama in self.data:
            print(f"{nama}: {self.data[nama]}")
        else:
            print("Nama mahasiswa tidak ditemukan.")

    def urutkan(self):
        if not self.data:
            print("Data masih kosong.")
        else:
            print("Data mahasiswa yang sudah diurutkan:")
            for nama, nilai in sorted(self.data.items(), key=lambda item: item[1], reverse=True):
                print(f"{nama}: {nilai}")

    def main():
    daftar_nilai = DaftarNilai()

    while True:
        print("\nMenu:")
        print("1. Tambah data")
        print("2. Tampilkan data")
        print("3. Hapus data")
        print("4. Ubah data")
        print("5. Cari data")
        print("6. Urutkan data")
        print("7. Keluar")

        pilihan = input("Pilih menu: ")

        if pilihan == '1':
            daftar_nilai.tambah()
        elif pilihan == '2':
            daftar_nilai.tampilkan()
        elif pilihan == '3':
            nama = input("Masukkan nama mahasiswa yang ingin dihapus: ")
            daftar_nilai.hapus(nama)
        elif pilihan == '4':
            nama = input("Masukkan nama mahasiswa yang ingin diubah: ")
            daftar_nilai.ubah(nama)
        elif pilihan == '5':
            nama = input("Masukkan nama mahasiswa yang ingin dicari: ")
            daftar_nilai.cari(nama)
        elif pilihan == '6':
            daftar_nilai.urutkan()
        elif pilihan == '7':
            print("Keluar dari program.")
            break
        else:
            print("Pilihan tidak valid.")

    if __name__ == "__main__":
    main()
