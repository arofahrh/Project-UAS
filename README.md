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
1. Modul Data.
   tujuan : class user ini digunakan untuk membuat objek yang menyimpan informasi tentang seorang pengguna.
   - _init_ method 
	  ini adalah konstruktor yang akan dijalankan setiap kali kita membuka objek user. Di sini,
    menyimpan 4 data yaitu : name, age, favorite_series, dan favorite_movie.
	- _str_ method : method ini digunakan untuk mengubah objek menjadi format string. Jadi, saat kita ingin menampilkan data pengguna,
   program akan memanggil method ini dan menampilkan informasi pengguna format yang rapi. 
2. 
        



      
  
