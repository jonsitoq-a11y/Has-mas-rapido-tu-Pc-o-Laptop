# ====================================================================
# SCRIPT DE OPTIMIZACIÓN DEL SISTEMA
# Creado para el Asistente de Programación
# ====================================================================

# --------------------------------------------------------------------
# 1. Limpieza de archivos temporales
# --------------------------------------------------------------------
Write-Host "Paso 1: Limpiando archivos temporales..." -ForegroundColor Yellow

# Define la ruta a la carpeta temporal del usuario
$TempPath = Get-Item -Path "$env:TEMP"

# Borra los archivos y carpetas dentro de la carpeta temporal
# El parámetro -ErrorAction SilentlyContinue evita que el script se detenga si algún archivo está en uso.
Remove-Item -Path "$TempPath\*" -Recurse -Force -ErrorAction SilentlyContinue

Write-Host "Limpieza de temporales finalizada." -ForegroundColor Green

# --------------------------------------------------------------------
# 2. Optimización del disco duro
# --------------------------------------------------------------------
Write-Host "Paso 2: Optimizando las unidades de disco..." -ForegroundColor Yellow

# 'Get-Volume' obtiene una lista de todas las unidades de disco.
# El comando 'Optimize-Volume' optimiza la unidad. En discos duros (HDD) desfragmenta,
# y en discos de estado sólido (SSD) ejecuta un comando de optimización llamado TRIM.
Get-Volume | Where-Object { $_.DriveType -eq 'Fixed' } | Optimize-Volume -Verbose

Write-Host "Optimización de discos finalizada." -ForegroundColor Green

# --------------------------------------------------------------------
# 3. Identificación de programas de inicio
# --------------------------------------------------------------------
Write-Host "Paso 3: Identificando programas de inicio lentos..." -ForegroundColor Yellow
Write-Host "A continuación se muestra una lista de programas que se inician con Windows."
Write-Host "Puedes revisar esta lista para decidir cuáles desactivar desde el Administrador de Tareas."
Write-Host ""

# 'Get-CimInstance' obtiene información sobre los programas que se inician con Windows.
# 'Sort-Object' los ordena por nombre para que sea más fácil de leer.
Get-CimInstance Win32_StartupCommand | Sort-Object Name | Format-Table Name, Location -AutoSize

Write-Host ""
Write-Host "Análisis completado. Los cambios que hagas en el Administrador de Tareas te ayudarán a acelerar el inicio de tu PC." -ForegroundColor Cyan
