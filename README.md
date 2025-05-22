Arch Linux Auto-Installer 🔐🚀

Instalador automatizado de Arch Linux con cifrado LUKS2, LVM y systemd-boot
Características principales:
✅ Cifrado completo del sistema con LUKS2
✅ Gestión de volúmenes LVM
✅ Boot UEFI con systemd-boot
✅ Soporte para múltiples kernels y microcódigos
✅ Configuración automática de drivers gráficos

Instalación Segura
Entornos
🌟 Novedades en esta versión

    Reemplazo de GRUB por systemd-boot para sistemas UEFI modernos

    Cifrado LUKS2 con parámetros seguros (Argon2id, SHA3-512)

    Borrado seguro del disco con datos aleatorios

    Soporte para discos NVMe y TRIM (opcional)

    Menú interactivo para selección de entornos gráficos

🛠️ Requisitos del Sistema

    UEFI (no soporta BIOS legacy)

    Conexión a Internet (recomendado cable Ethernet)

    Mínimo 10 GB de espacio en disco

    USB booteable con Arch Linux

📥 Preparación del Entorno Live

```bash
pacman -Sy git
git clone https://github.com/SolimanHub/arch_crypt
cd arch
chmod +x start scripts/*
```
🖥️ Flujo de Instalación
1. Ejecutar instalador principal

```bash
./start
```
2. Proceso Automatizado

    Configuración inicial

        Selección de disco y borrado seguro

        Creación de particiones cifradas

        Configuración de LVM (swap, root, home opcional)

    Configuración del Sistema

        Elección de kernels (Standard, Zen, LTS)

        Selección de entorno gráfico (i3, GNOME, KDE, etc)

        Detección automática de microcódigo (Intel/AMD)

        Configuración de zona horaria e idioma

    Post-Instalación

        Instalación de drivers gráficos (NVIDIA/AMD/Intel)

        Configuración de usuarios y permisos

        Instalación básica de ZSH + Oh My ZSH

        Habilitación de servicios esenciales

🔧 Estructura de Scripts Principales
Script	Función
particionar_montar	Cifrado LUKS2, creación de LVM y montaje de particiones
systemd_boot	Instalación y configuración del bootloader UEFI
datos	Interfaz interactiva para configuración del sistema
extras	Instalación de drivers y entornos gráficos
usuarios	Creación de usuarios y configuración de permisos
zsh	Instalación personalizada de ZSH con plugins
🛡️ Configuración de Seguridad

```bash
Parámetros de cifrado LUKS2

cryptsetup luksFormat --type luks2
--pbkdf argon2id
--iter-time 4000
--key-size 512
--hash sha3-512
```

Características incluidas:

    Cifrado AES-XTS de 512 bits

    Derivación de claves con Argon2id

    Protección contra ataques de fuerza bruta

    Soporte para TRIM en SSDs (opcional)

🚦 Troubleshooting
Error al detectar disco

```bash
Verificar nombre del disco

lsblk -d -o NAME,SIZE,TYPE
```
Recuperar acceso al sistema cifrado

```bash
cryptsetup open /dev/nvme0n1p2 cryptlvm
mount /dev/vol01/root /mnt
```
Regenerar initramfs

```bash
mkinitcpio -P
```
📌 Notas Importantes

    SSD Optimization: Agregar :allow-discards al parámetro cryptdevice si necesitas TRIM

    Kernels Alternativos: Los kernels Zen/LTS requieren configuración manual en entries

    Soporte NVIDIA: Se instala automáticamente si se detecta hardware NVIDIA

📚 Recursos Adicionales

    [Guía LUKS2](https://wiki.archlinux.org/title/Dm-crypt/Device_encryption)

    [systemd-boot](https://wiki.archlinux.org/title/Systemd-boot)

    [LVM Best Practices](https://wiki.archlinux.org/title/LVM)

📞 Soporte

¿Problemas con la instalación?
Contacto Telegram: @Softliman
Issues: GitHub Issues
