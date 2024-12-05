# labpy8

    class Mahasiswa:
    def __init__(self):
        self.__data_mahasiswa = []  # Private attribute untuk menyimpan data mahasiswa

    def tambah(self, nama, nim, tugas, uts, uas):
        """Method untuk menambah data mahasiswa"""
        nilai_akhir = (tugas * 0.3) + (uts * 0.35) + (uas * 0.35)
        self.__data_mahasiswa.append({
            'nama': nama,
            'nim': nim,
            'tugas': tugas,
            'uts': uts,
            'uas': uas,
            'akhir': round(nilai_akhir, 2)
        })

    def tampilkan(self):
        """Method untuk menampilkan data mahasiswa"""
        if not self.__data_mahasiswa:
            print("\nTidak ada data mahasiswa.")
        else:
            print("\nDaftar Nilai Mahasiswa:")
            print("=======================================================")
            print("| No | NIM    | Nama      | Tugas | UTS | UAS | Akhir |")
            print("=======================================================")
            for i, mhs in enumerate(self.__data_mahasiswa, start=1):
                print(f"| {i:<2} | {mhs['nim']:<6} | {mhs['nama']:<9} | "
                      f"{mhs['tugas']:<5} | {mhs['uts']:<3} | {mhs['uas']:<3} | {mhs['akhir']:<5} |")
            print("=======================================================")

    def hapus(self, nama):
        """Method untuk menghapus data mahasiswa berdasarkan nama"""
        for mhs in self.__data_mahasiswa:
            if mhs['nama'].lower() == nama.lower():
                self.__data_mahasiswa.remove(mhs)
                print(f"\nData mahasiswa atas nama {nama} telah dihapus.")
                return
        print(f"\nData mahasiswa atas nama {nama} tidak ditemukan.")

    def ubah(self, nama):
        """Method untuk mengubah data mahasiswa berdasarkan nama"""
        for mhs in self.__data_mahasiswa:
            if mhs['nama'].lower() == nama.lower():
                print(f"\nUbah data mahasiswa atas nama {nama}:")
                mhs['nim'] = input("Masukkan NIM baru: ")
                mhs['tugas'] = int(input("Masukkan nilai tugas baru: "))
                mhs['uts'] = int(input("Masukkan nilai UTS baru: "))
                mhs['uas'] = int(input("Masukkan nilai UAS baru: "))
                mhs['akhir'] = round((mhs['tugas'] * 0.3) + (mhs['uts'] * 0.35) + (mhs['uas'] * 0.35), 2)
                print("\nData berhasil diubah.")
                return
        print(f"\nData mahasiswa atas nama {nama} tidak ditemukan.")


    # Subclass untuk pewarisan
    class Person(Mahasiswa):
    def __init__(self):
        super().__init__()

    def cetak_data(self):
        """Method untuk mencetak data mahasiswa (contoh overriding)"""
        print("\nMemanggil method cetak_data dari class Person.")
        super().tampilkan()


    # Menu program
    def menu():
    daftar = Mahasiswa()

    while True:
        print("\nProgram Input Nilai Mahasiswa")
        print("1. Tambah Data")
        print("2. Tampilkan Data")
        print("3. Hapus Data")
        print("4. Ubah Data")
        print("5. Keluar")
        pilihan = input("Pilih menu: ")

        if pilihan == "1":
            nama = input("\nMasukkan Nama: ")
            nim = input("Masukkan NIM: ")
            tugas = int(input("Masukkan Nilai Tugas: "))
            uts = int(input("Masukkan Nilai UTS: "))
            uas = int(input("Masukkan Nilai UAS: "))
            daftar.tambah(nama, nim, tugas, uts, uas)
        elif pilihan == "2":
            daftar.tampilkan()
        elif pilihan == "3":
            nama = input("\nMasukkan Nama Mahasiswa yang Ingin Dihapus: ")
            daftar.hapus(nama)
        elif pilihan == "4":
            nama = input("\nMasukkan Nama Mahasiswa yang Ingin Diubah: ")
            daftar.ubah(nama)
        elif pilihan == "5":
            print("\nTerima kasih telah menggunakan program ini.")
            break
        else:
            print("\nPilihan tidak valid. Coba lagi.")


    if __name__ == "__main__":
    menu()
