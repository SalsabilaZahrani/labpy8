# labpy8

Tugas Praktikum

Buat program sederhana dengan mengaplikasikan penggunaan class. Buatlah
class untuk menampilkan daftar nilai mahasiswa, dengan ketentuan:
1. Method tambah() untuk menambah data
2. Method tampilkan() untuk menampilkan data
3. Method hapus(nama) untuk menghapus data berdasarkan nama
4. Method ubah(nama) untuk mengubah data berdasarkan nama
5. Buat diagram class, flowchart dan penjelasan programnya pada README.md.
6. Commit dan push repository ke github.

        class DaftarNilaiMahasiswa:
        def __init__(self):  
        self.mahasiswa = {}

        def tambah(self, nama, nilai):
        """Menambah data mahasiswa."""
        self.mahasiswa[nama] = nilai
        print(f"Data {nama} dengan nilai {nilai} berhasil ditambahkan.")

        def tampilkan(self):
        """Menampilkan semua data mahasiswa."""
        if not self.mahasiswa:
            print("Tidak ada data mahasiswa.")
        else:
            print("Daftar Nilai Mahasiswa:")
            for nama, nilai in self.mahasiswa.items():
                print(f"Nama: {nama}, Nilai: {nilai}")

        def hapus(self, nama):
        """Menghapus data mahasiswa berdasarkan nama."""
        if nama in self.mahasiswa:
            del self.mahasiswa[nama]
            print(f"Data {nama} berhasil dihapus.")
        else:
            print(f"Data {nama} tidak ditemukan.")

        def ubah(self, nama, nilai_baru): 
         """Mengubah data mahasiswa berdasarkan nama."""
        if nama in self.mahasiswa:
            self.mahasiswa[nama] = nilai_baru
            print(f"Data {nama} berhasil diubah menjadi nilai {nilai_baru}.")
        else:
            print(f"Data {nama} tidak ditemukan.")

        def main():
        daftar = DaftarNilaiMahasiswa()

        while True:
        print("\nMenu:")
        print("1. Tambah Data")
        print("2. Tampilkan Data")
        print("3. Hapus Data")
        print("4. Ubah Data")
        print("5. Keluar")

        pilihan = input("Pilih menu: ")

        if pilihan == '1':
            nama = input("Masukkan nama mahasiswa: ")
            try:
                nilai = int(input("Masukkan nilai mahasiswa: "))
                daftar.tambah(nama, nilai)
            except ValueError:
                print("Nilai harus berupa angka.")
        elif pilihan == '2':
            daftar.tampilkan()
        elif pilihan == '3':
            nama = input("Masukkan nama mahasiswa yang ingin dihapus: ")
            daftar.hapus(nama)
        elif pilihan == '4':
            nama = input("Masukkan nama mahasiswa yang ingin diubah: ")
            try:
                nilai_baru = int(input("Masukkan nilai baru: "))
                daftar.ubah(nama, nilai_baru)
            except ValueError:
                print("Nilai harus berupa angka.")
        elif pilihan == '5':
            print("Keluar dari program.")
            break
        else:
            print("Pilihan tidak valid. Silakan coba lagi.")

        if __name__ == "__main__":
        main()

INPUT
![Cuplikan layar 2024-12-05 154202](https://github.com/user-attachments/assets/6aa0a771-e68f-40e4-9861-4590d734e647)
![Cuplikan layar 2024-12-05 154223](https://github.com/user-attachments/assets/600b9670-b9c0-4ec1-bf7e-8884565397c1)
![Cuplikan layar 2024-12-05 154244](https://github.com/user-attachments/assets/fe49ce5d-c4e3-439c-a5d2-132a503655a2)

OUTPUT
![Cuplikan layar 2024-12-05 154740](https://github.com/user-attachments/assets/b505347e-77d6-42c0-a41e-718038a33620)
![Cuplikan layar 2024-12-05 154800](https://github.com/user-attachments/assets/9d6410bf-7998-4707-af4c-a65064312a98)

PENJELASAN!
1. Tambah Data: Menyimpan nama dan nilai mahasiswa ke dalam dictionary.
2. Tampilkan Data: Menampilkan semua data mahasiswa dalam format daftar.
3. Hapus Data: Menghapus data mahasiswa berdasarkan nama berdasarkan nama.
4. Ubah Data: Mengupdate nilai mahasiswa berdasarkan nama.
Program menyediakan menu interaktif berbasis teks untuk pengguna, berjalan dalam loop hingga memilih opsi Keluar.

FLOWCHART
![flowchart3](https://github.com/user-attachments/assets/35cdaa06-a9b3-4273-b567-9484b9439ccc)
