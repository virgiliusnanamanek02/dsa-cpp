# Deque

### Sliding Window

```cpp
#include <deque>
#include <iostream>
#include <vector>

// Fungsi untuk mencari maksimum di setiap jendela
std::vector<int> maxSlidingWindow(const std::vector<int>& nums, int k)
{
  // Digunakan untuk menyimpan indeks elemen yang mungkin menjadi maksimum.
  // Elemen di deque akan selalu terurut menurun berdasarkan nilainya.
  std::deque<int> d;
  std::vector<int> result; // Vektor untuk menyimpan hasil maksimum setiap jendela
  int n = nums.size();

  // 1. Proses Jendela Pertama (Inisialisasi)
  for (int i = 0; i < k; ++i)
  {
    // Hapus indeks dari belakang jika nilai yang baru (nums[i]) lebih besar
    // dari nilai pada indeks yang ada di belakang deque.
    // Ini memastikan elemen terbesar selalu di depan.
    while (!d.empty() && nums[i] >= nums[d.back()])
    {
      d.pop_back();
    }
    // Tambahkan indeks saat ini
    d.push_back(i);
  }

  // Maksimum dari jendela pertama adalah elemen di depan deque.
  result.push_back(nums[d.front()]);

  // 2. Proses Jendela Selanjutnya (Geser Jendela)
  for (int i = k; i < n; ++i)
  {

    // a. Hapus Indeks yang Kadaluarsa (Keluar dari Jendela)
    // Jika indeks terdepan berada di luar batas jendela saat ini (i - k),
    // hapus dari depan (O(1)).
    if (!d.empty() && d.front() <= i - k)
    {
      d.pop_front();
    }

    // b. Pertahankan Urutan Menurun
    // Hapus indeks dari belakang jika nilai yang baru (nums[i]) lebih besar.
    while (!d.empty() && nums[i] >= nums[d.back()])
    {
      d.pop_back();
    }

    // c. Tambahkan Indeks Baru
    d.push_back(i);

    // d. Catat Maksimum
    // Maksimum untuk jendela saat ini selalu berada di depan deque.
    result.push_back(nums[d.front()]);
  }

  return result;
}

int main()
{
  std::vector<int> data = {1, 3, -1, -3, 5, 3, 6, 7};
  int window_size = 3;

  std::vector<int> maksimum = maxSlidingWindow(data, window_size);

  std::cout << "Data Array: [";
  for (size_t i = 0; i < data.size(); ++i)
  {
    std::cout << data[i] << (i == data.size() - 1 ? "" : ", ");
  }
  std::cout << "]\n";
  std::cout << "Ukuran Jendela (k): " << window_size << "\n";

  std::cout << "Maksimum di Setiap Jendela: [";
  for (size_t i = 0; i < maksimum.size(); ++i)
  {
    std::cout << maksimum[i] << (i == maksimum.size() - 1 ? "" : ", ");
  }
  std::cout << "]\n";

  /* Proses Jendela (k=3):
  [1, 3, -1] -> Max: 3
  [3, -1, -3] -> Max: 3
  [-1, -3, 5] -> Max: 5
  [-3, 5, 3] -> Max: 5
  [5, 3, 6] -> Max: 6
  [3, 6, 7] -> Max: 7
  Hasil: [3, 3, 5, 5, 6, 7]
  */

  return 0;
}
```
