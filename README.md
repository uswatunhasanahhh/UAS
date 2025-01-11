# Project-UAS
## Link URL Video
(https://youtu.be/I64vCCEJyqs?si=LYR6rwPEZqnx4HQC)
```
class Data:
    """
    Class untuk mengelola data yang dimasukkan pengguna.
    """
    def _init_(self):
        self.records = []

    def add_record(self, name, age, profession):
        self.records.append({"name": name, "age": age, "profession": profession})


class View:
    """
    Class untuk menangani tampilan hasil.
    """
    @staticmethod
    def display_table(records):
        if not records:
            print("\nNo data available.")
            return

        print("\n| Name           | Age  | Profession      |")
        print("+----------------+------+-----------------+")
        for record in records:
            print(f"| {record['name']:<14} | {record['age']:<4} | {record['profession']:<15} |")
        print("+----------------+------+-----------------+")

    @staticmethod
    def show_error(message):
        print(f"Error: {message}")
class Process:
    """
    Class untuk memproses data dari input pengguna.
    """
    def _init_(self, data):
        self.data = data

    def add_data(self):
        try:
            name = input("Enter name: ").strip()
            if not name:
                raise ValueError("Name cannot be empty.")

            age = input("Enter age: ").strip()
            if not age.isdigit():
                raise ValueError("Age must be a number.")
            age = int(age)
            if age <= 0:
                raise ValueError("Age must be greater than zero.")

            profession = input("Enter profession: ").strip()
            if not profession:
                raise ValueError("Profession cannot be empty.")

            self.data.add_record(name, age, profession)

        except ValueError as e:
            View.show_error(e)
# Main program
def main():
    data = Data()
    process = Process(data)

    while True:
        print("\nMenu:")
        print("1. Add Data")
        print("2. Show Data")
        print("3. Exit")

        choice = input("Choose an option: ").strip()

        if choice == "1":
            process.add_data()
        elif choice == "2":
            View.display_table(data.records)
        elif choice == "3":
            print("Goodbye!")
            break
        else:
            print("Invalid choice. Please try again.")


if _name_ == "_main_":
    main()

```
# 1. Kelas Data
Tujuan: Mengelola penyimpanan data.
Atribut:
self.records: Sebuah daftar (list) yang berisi data pengguna dalam bentuk kamus.
Metode:
add_record(name, age, profession): Menambahkan data berupa nama, umur, dan profesi ke dalam daftar records.
# 2. Kelas View
Tujuan: Menangani tampilan data dan pesan kesalahan.
Metode:
display_table(records):
Menampilkan data dalam format tabel.
Jika tidak ada data, menampilkan pesan bahwa data kosong.
show_error(message):
Menampilkan pesan kesalahan dalam format "Error: {pesan}".
# 3. Kelas Process
Tujuan: Mengelola proses input data dari pengguna.
Atribut:
self.data: Mengacu pada objek kelas Data untuk menyimpan data yang telah diproses.
Metode:
add_data():
Menerima input dari pengguna untuk nama, umur, dan profesi.
Melakukan validasi:
Nama tidak boleh kosong.
Umur harus angka yang lebih besar dari 0.
Profesi tidak boleh kosong.
Jika validasi gagal, menampilkan pesan kesalahan menggunakan View.show_error.
Jika validasi berhasil, data ditambahkan ke dalam objek Data menggunakan add_record.
# 4. Fungsi main()
Tujuan: Mengatur alur program.
Alur:
Membuat objek Data dan Process.
Menampilkan menu pilihan:
Add Data: Memanggil process.add_data() untuk menambahkan data pengguna.
Show Data: Memanggil View.display_table(data.records) untuk menampilkan semua data dalam tabel.
Exit: Keluar dari program.
Jika pengguna memilih opsi yang tidak valid, program meminta pengguna untuk mencoba lagi.
# 5. Cara Kerja Program
Saat dijalankan, pengguna diberikan pilihan menu.
Jika memilih "1. Add Data":
Program meminta pengguna memasukkan nama, umur, dan profesi.
Data divalidasi, lalu disimpan jika valid.
Jika memilih "2. Show Data":
Program menampilkan semua data yang sudah dimasukkan dalam bentuk tabel.
Jika memilih "3. Exit":
Program berhenti dan menampilkan pesan selamat tinggal.
Jika memasukkan pilihan yang salah, program akan meminta pengguna mencoba lagi.
Contoh Interaksi
Input:
plaintext
Copy code
Menu:
1. Add Data
2. Show Data
3. Exit
Choose an option: 1
Enter name: Alice
Enter age: 25
Enter profession: Engineer
Output:
plaintext
Copy code
Data added successfully.
Input:
plaintext
Copy code
Menu:
1. Add Data
2. Show Data
3. Exit
Choose an option: 2
Output:
plaintext
Copy code
| Name           | Age  | Profession      |
+----------------+------+-----------------+
| Alice          | 25   | Engineer        |
+----------------+------+-----------------+
# Keunggulan
Pemrograman Berorientasi Objek: Kode terstruktur dengan baik menggunakan kelas.
Modularitas: Logika penyimpanan, tampilan, dan pemrosesan dipisahkan dalam kelas yang berbeda.
Validasi Input: Program memastikan data yang dimasukkan valid sebelum menyimpannya.
Peningkatan yang Mungkin
Tambahkan fitur untuk menghapus atau memperbarui data.
Simpan data ke file agar tidak hilang setelah program ditutup.
Gunakan pustaka tabel seperti tabulate untuk tampilan tabel yang lebih rapi.
```
