# 🌸 Aira Kernel Builder ARM64

<p align="center">
  <img src="https://img.shields.io/badge/Arch-ARM64-blueviolet?style=for-the-badge&logo=android" alt="arch">
  <img src="https://img.shields.io/github/actions/workflow/status/ryucodelab/Aira-Kernel-Builder-ARM64-KSU-/build.yml?style=for-the-badge&label=Build" alt="build status">
  <img src="https://img.shields.io/github/v/release/ryucodelab/Aira-Kernel-Builder-ARM64-KSU-?style=for-the-badge&color=success" alt="release">
  <img src="https://img.shields.io/github/license/ryucodelab/Aira-Kernel-Builder-ARM64-KSU-?style=for-the-badge" alt="license">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Clang-Neutron%20%7C%20Proton%20%7C%20AOSP%20%7C%20WeebX%20%7C%20ZyC-orange?style=flat-square">
  <img src="https://img.shields.io/badge/KernelSU-Optional-lightgrey?style=flat-square">
  <img src="https://img.shields.io/badge/LTO-Thin%20%7C%20Full-blue?style=flat-square">
</p>

Kernel builder generic buat **device Android ARM64 mana aja**, tinggal isi form — gak perlu setup toolchain manual, gak perlu clone-clone sendiri. Semua jalan otomatis lewat GitHub Actions.

Cukup isi:
- URL & branch kernel source
- Defconfig
- URL AnyKernel3
- Pilihan Clang toolchain
- Enable/disable KernelSU

Klik **Run workflow**, tunggu, hasil zip flashable otomatis muncul di **Releases**.

---

## ✨ Fitur

- 📋 **Form input langsung dari GitHub UI** (`workflow_dispatch`) — gak perlu edit YAML tiap mau build device beda
- 🧰 **Multi-clang**: Neutron, Proton, AOSP, WeebX, ZyC, atau custom URL sendiri
- 🩹 **KernelSU toggle**: pilih `none`, `KernelSU`, atau `KernelSU-Next`
- 🚀 **LTO support**: none / thin / full
- 🔍 **Auto-detect output image** — support `Image`, `Image.gz`, `Image-dtb`, `Image.gz-dtb`, jadi gak hardcode per device
- 📦 **Auto-pack AnyKernel3** jadi zip flashable
- 🚀 **Auto-release** ke GitHub Releases + upload artifact & build log buat debug
- ⚡ **Cache toolchain clang** biar build berikutnya lebih cepet

---

## 🚀 Cara Setup

### 1. Fork / clone repo ini

```bash
git clone https://github.com/ryucodelab/Aira-Kernel-Builder-ARM64-KSU-.git
```

### 2. Taruh workflow

Pastikan file workflow ada di:

```
.github/workflows/build.yml
```

### 3. Jalankan build

1. Buka tab [**Actions**](https://github.com/ryucodelab/Aira-Kernel-Builder-ARM64-KSU-/actions/workflows/build.yml) di repo ini
2. Pilih workflow **🛠️ Build Android Kernel**
3. Klik **Run workflow**
4. Isi form yang muncul:

| Input | Contoh | Keterangan |
|---|---|---|
| `KERNEL_URL` | `https://github.com/xxx/kernel_xiaomi_lavender` | URL git kernel source |
| `KERNEL_BRANCH` | `lineage-20` | Branch kernel |
| `KERNEL_DEFCONFIG` | `lavender_defconfig` | Nama defconfig |
| `ANYKERNEL3_URL` | `https://github.com/osm0sis/AnyKernel3` | Repo AnyKernel3 |
| `CLANG_SOURCE` | `neutron` | neutron / proton / aosp / weebx / zyc / custom |
| `CUSTOM_CLANG_URL` | *(opsional)* | Kalau pilih `custom` |
| `USE_KSU` | `KernelSU-Next` | none / KernelSU / KernelSU-Next |
| `USE_LTO` | `thin` | none / thin / full |
| `LOCALVERSION` | `-AiraBuild` | Opsional |
| `ARCH` | `arm64` | arm64 / arm |

5. Klik **Run workflow** hijau, tunggu build selesai
6. Hasil zip flashable otomatis ada di tab **Releases** dan **Artifacts**

---

## 🔧 Troubleshooting

- **Build gagal nemu image** → cek `build.log` di artifact, biasanya defconfig salah atau path output beda dari yang di-detect
- **Clang error karena kernel lama** → coba ganti `CLANG_SOURCE` ke `proton` (lebih battle-tested buat kernel lawas)
- **KernelSU gagal apply** → pastikan kernel source support KSU patch (beberapa kernel butuh manual patch tambahan kayak susfs)

---

## 🙏 Credits

- [Neutron Clang](https://github.com/Neutron-Toolchains/antman) — toolchain
- [kdrag0n/proton-clang](https://github.com/kdrag0n/proton-clang)
- [XSans0/WeebX-Clang](https://github.com/XSans0/WeebX-Clang)
- [ZyCromerZ/Clang](https://github.com/ZyCromerZ/Clang)
- [osm0sis/AnyKernel3](https://github.com/osm0sis/AnyKernel3)
- [tiann/KernelSU](https://github.com/tiann/KernelSU)
- [KernelSU-Next](https://github.com/KernelSU-Next/KernelSU-Next)

---

<p align="center">Made with 🌸 by <b>Ryu</b></p>
