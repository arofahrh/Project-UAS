# Project-UAS
[link youtube](https://youtu.be/urpqpQ08dJc)
  ## kode program :
      1. modul data :
            class User:
                def __init__(self, name, age, favorite_series, favorite_movie):
                    self.name = name
                    self.age = age
                    self.favorite_series = favorite_series
                    self.favorite_movie = favorite_movie
    
        def __str__(self):
            return f"{self.name:<20} | {self.age:<5} | {self.favorite_series:<20} | {self.favorite_movie:<20}"
            
      2. modul process :
                from data import User
              class Process:
                  @staticmethod
                  def create_user(name, age, favorite_series, favorite_movie):
                      # Validasi usia, jika tidak valid maka beri pengecualian
                      if age < 0:
                          raise ValueError("Age cannot be negative.")
              
                  return User(name, age, favorite_series, favorite_movie)

      3. modul view :
          class View:
        @staticmethod
        def display_table(users):
            print(f"{'Name':<20} | {'Age':<5} | {'Favorite Series':<20} | {'Favorite Movie':<20}")
            print("=" * 80)
            for user in users:
                print(user)
    
        @staticmethod
        def get_user_input():
            try:
                name = input("Enter your name: ")
                age = int(input("Enter your age: "))
                favorite_series = input("Enter your favorite series: ")
                favorite_movie = input("Enter your favorite movie: ")
                return name, age, favorite_series, favorite_movie
            except ValueError:
                raise ValueError("Age must be a valid integer.")

    4. modul main :
    from view import View
    from process import Process
    
    def main():
        users = []
        
    while True:
        try:
            # Minta input pengguna
            name, age, favorite_series, favorite_movie = View.get_user_input()

            # Proses input dan buat objek User
            user = Process.create_user(name, age, favorite_series, favorite_movie)

            # Tambahkan user ke daftar
            users.append(user)

            # Tanyakan apakah pengguna ingin memasukkan data lagi
            continue_input = input("Do you want to add another user? (y/n): ").strip().lower()
            if continue_input != 'y':
                break
        except ValueError as e:
            print(f"Error: {e}")
    
    # Tampilkan hasil dalam bentuk tabel
    View.display_table(users)

    # Memulai program
    if __name__ == "__main__":
        main()

  ## penjelasan kode program :
1. Modul Data,
   tujuan : class user ini digunakan untuk membuat objek yang menyimpan informasi tentang seorang pengguna.
   - _init_ method 
	  ini adalah konstruktor yang akan dijalankan setiap kali kita membuka objek user. Di sini,
    menyimpan 4 data yaitu : name, age, favorite_series, dan favorite_movie.
	- _str_ method : method ini digunakan untuk mengubah objek menjadi format string. Jadi, saat kita ingin menampilkan data pengguna,
   program akan memanggil method ini dan menampilkan informasi pengguna format yang rapi. 
2. Modul view,
   Tujuan: class view ini mengatur input dan output, berfungsi untuk berinteraksi dengan pengguna.
  - Display_table method: ini digunakan untuk menampilkan data pengguna dalam bentuk tabel.
    Dimulai dengan menampilkan header tabel dan kemudian menampilkan setiap pengguna yang ada dalam list users.
  - Get_user_input :  ini digunakan untuk meminta input dari pengguna. Pengguna diminta memasukkan nama, usia, seri favorit, dan film favorit.
    Jika ada kesalahan dalam memasukkan usia (misalnya memasukkan string alih-alih angka), program akan menampilkan pesan error.
3. Modul process, 
   Tujuan : mengelola logika pemrosesan data pengguna, seperti validasi usia dan pembuatan objek user.
  - Create_user :  ini adalah method statis (ini tuh artinya bisa dipanggil tanpa perlu membuat objek process) nah ini yang menerima input nama, usia, seri favorit, dan 
    film favorit. Jika usia yang dimasukkan negatif, program akan menampilkan pesan error. Jika valid, method ini akan mengembalikan objek user.
4. Modul main, 
   Tujuan : adalah bagian utama dari program yang mengatur alur kerja.
   - Process pengumpulan data : program akan terus meminta input pengguna hingga pengguna memilih untuk berhenti.
     Input pengguna akan diproses untuk membuat objek user dan ditambahkan ke list users.
   - Handling error : terjadi error (misalnya usia negatif atau input usia yang bukan angka), program akan menangani exception tersebut dan memberi tahu pengguna dengan 
     pesan error yang sesuai.
   - Tanya Pengguna untuk Input Berikutnya: Setelah satu pengguna selesai dimasukkan, program akan menanyakan apakah pengguna ingin menambah data lain.
     Jika jawabannya "y", maka input akan diminta lagi; jika "n", program akan berhenti.
   - Menampilkan Data: Setelah semua data dimasukkan, program akan menampilkan tabel yang berisi semua data pengguna yang telah dimasukkan.
   - Bagian main
     Tujuan: Bagian ini memastikan bahwa main() hanya dijalankan jika program dijalankan langsung, bukan jika diimpor sebagai modul di program lain.




        



      
  
