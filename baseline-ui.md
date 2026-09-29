---
name: baseline-ui
description: Merapikan UI dengan cepat dengan memperbaiki spacing, hierarki, tipografi, dan masalah layout kecil. Gunakan ketika tampilan membutuhkan pembersihan atau penyempurnaan dengan cepat.
---

# Baseline UI

Menerapkan standar UI yang tegas untuk mencegah tampilan UI yang berantakan atau terlalu dibuat-buat oleh AI.

## Cara menggunakan

- `/baseline-ui`
  Terapkan semua aturan ini pada pekerjaan UI apa pun dalam percakapan ini.

- `/baseline-ui <file>`
  Periksa file berdasarkan semua aturan di bawah dan tampilkan:
  - pelanggaran (kutip baris/snippet yang tepat)
  - mengapa hal tersebut penting (1 kalimat singkat)
  - perbaikan konkret (saran pada level kode)

## Stack

- WAJIB menggunakan default Tailwind CSS kecuali nilai custom sudah digunakan atau memang diminta secara eksplisit
- WAJIB menggunakan `motion/react` (sebelumnya `framer-motion`) ketika animasi JavaScript diperlukan
- SEBAIKNYA menggunakan `tw-animate-css` untuk entrance animation dan micro-animation pada Tailwind CSS
- WAJIB menggunakan utility `cn` (`clsx` + `tailwind-merge`) untuk logika class

## Components

- WAJIB menggunakan primitive komponen yang aksesibel untuk segala sesuatu yang memiliki perilaku keyboard atau focus (`Base UI`, `React Aria`, `Radix`)
- WAJIB menggunakan primitive komponen yang sudah digunakan oleh project terlebih dahulu
- JANGAN pernah mencampur sistem primitive dalam satu interaction surface
- SEBAIKNYA memilih [`Base UI`](https://base-ui.com/react/components) untuk primitive baru jika kompatibel dengan stack
- WAJIB menambahkan `aria-label` pada tombol yang hanya berisi icon
- JANGAN pernah membuat ulang perilaku keyboard atau focus secara manual kecuali memang diminta secara eksplisit

## Interaction

- WAJIB menggunakan `AlertDialog` untuk tindakan yang bersifat destruktif atau tidak dapat dibatalkan
- SEBAIKNYA menggunakan structural skeleton untuk loading state
- JANGAN menggunakan `h-screen`, gunakan `h-dvh`
- WAJIB memperhatikan `safe-area-inset` untuk elemen yang menggunakan posisi fixed
- WAJIB menampilkan error di dekat tempat aksi tersebut dilakukan
- JANGAN pernah memblokir fitur paste pada elemen `input` atau `textarea`

## Animation

- JANGAN pernah menambahkan animasi kecuali memang diminta secara eksplisit
- WAJIB hanya menganimasikan properti compositor (`transform`, `opacity`)
- JANGAN pernah menganimasikan properti layout (`width`, `height`, `top`, `left`, `margin`, `padding`)
- SEBAIKNYA menghindari animasi pada properti paint (`background`, `color`) kecuali untuk UI lokal berukuran kecil seperti text atau icon
- SEBAIKNYA menggunakan `ease-out` pada entrance animation
- JANGAN pernah melebihi `200ms` untuk interaction feedback
- WAJIB menghentikan looping animation ketika elemen berada di luar layar
- SEBAIKNYA menghormati `prefers-reduced-motion`
- JANGAN pernah menggunakan custom easing curve kecuali memang diminta secara eksplisit
- SEBAIKNYA menghindari animasi pada gambar berukuran besar atau full-screen surface

## Typography

- WAJIB menggunakan `text-balance` untuk heading dan `text-pretty` untuk body/paragraf
- WAJIB menggunakan `tabular-nums` untuk data
- SEBAIKNYA menggunakan `truncate` atau `line-clamp` untuk UI yang padat
- JANGAN pernah mengubah `letter-spacing` (`tracking-*`) kecuali memang diminta secara eksplisit

## Layout

- WAJIB menggunakan skala `z-index` yang tetap (tidak boleh menggunakan `z-*` dengan nilai sembarang)
- SEBAIKNYA menggunakan `size-*` untuk elemen berbentuk persegi daripada menggunakan kombinasi `w-*` + `h-*`

## Performance

- JANGAN pernah menganimasikan area besar yang menggunakan `blur()` atau `backdrop-filter`
- JANGAN pernah menerapkan `will-change` di luar animasi yang sedang aktif
- JANGAN pernah menggunakan `useEffect` untuk sesuatu yang sebenarnya dapat diekspresikan melalui render logic

## Design

- JANGAN pernah menggunakan gradient kecuali memang diminta secara eksplisit
- JANGAN pernah menggunakan gradient berwarna ungu atau gradient dengan banyak warna
- JANGAN pernah menggunakan efek glow sebagai affordance utamaucing new ones
