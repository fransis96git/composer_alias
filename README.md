# composer_alias powershell
alias: 
Edit file berikut
```
C:\Users\<NamaPengguna>\Documents\WindowsPowerShell
```
jika belum ada:
```
mkdir $HOME\Documents\PowerShell
```
Kemudian:
```
New-Item -Type File -Force $PROFILE
```
Buat file baru:
```

subl $PROFILE
```

alias untuk cerate project dengan output lebih “minimal”.  
misal kita buat alias ``composer-cp`` di script ini:  
```
function composer-cp {
    param([string]$projectName)
    Write-Host "Membuat project Laravel baru: $projectName tanpa migrate..."
    
    # Buat project tanpa scripts
    composer create-project laravel/laravel $projectName --no-scripts
    
    # Masuk ke folder project
    Set-Location $projectName
    
    # Install dependency tanpa scripts
    composer install --no-scripts
    
    Write-Host "`nProject $projectName siap! Jalankan 'php artisan key:generate' dan 'php artisan migrate' manual jika perlu."
}
```

Berikutnya:
```
. $PROFILE
```
Uji coba misal:
```
composer-cp provinsi
```
