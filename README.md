<h1> Entorno-Linux/Ubuntu-Dependencias <b>20.04</b></h1>
<p>Dependencias comunes para un entorno Linux/Ubuntu, python, c++, github, vscode, wget, etcétera.<br>
<b>Nota:</b> Algunas dependencias se incluyen dentro de otras.</p>

<h2>Dependencias básicas</h2>
<p>Algunas dependencias básicas, dentro de estas se consideran:<br>
<b>wget</b> permite descargar contenido por links.<br>
<b>gpg</b> permite encriptado de datos.<br>
<b>dkms linux-headers-$(uname -r)</b> en el caso de utilizar Virtual Box.<br>
<b>gcc</b> y <b> make</b> permiten compilar códigos C.<br>
</p>

```bash
sudo apt update
sudo apt-get istall wget gpg
sudo apt install build-essential dkms linux-headers-$(uname -r)
sudo apt-get install build-essential gcc make
```

<h2>En el caso de instalar Virtual Box</h2>
<p>Un posible problema y su solución es el siguiente:</p>

```red
E: No se pudo obtener un bloqueo /var/lib/dpkg/lock-frontend - Ubuntu - 20.04 - DG
```
<a href="https://www.youtube.com/watch?v=NghoUNk2QVQ&ab_channel=DavidGuevara">->  solución</a>:

```bash
sudo fuser -vki /var/lib/dpkg/lock-frontend
sudo rm -f /var/lib/dpkg/lock-frontend
sudo dpkg --configure -a
sudo apt autoremove
```

<h2>C++</h2>
<p>A diferencia de <b>gcc</b>, <b>g++</b> permite linkear librerías propias de C++; se recomienda utilizar g++ para facilitar un poco el compilado de <b>C++</b>.<br>
<a href="https://stackoverflow.com/questions/172587/what-is-the-difference-between-g-and-gcc">referencia</a></p>

```bash
sudo apt-get install g++
```

<h2>PYTHON USING APT</h2>
<p></p>

```bash
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt install python3.8.12
```
<p><b>O bien puedes utilizar:</b></p>

```bash
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt-get update
sudo apt-get install python3.8
```

<h2>VSCODE</h2>
<p><b>Visual Studio Code</b> es un <b>editor de código fuente</b>, te ayudará junto a extensiones trabajar mejor visualmente con Python, C++, Java, R, SSH, etcétera.<br>
Viendo errores de sintáxis, fácilitando su ejecución, y haciendo más sencillo el manejo de varios lenguajes con esta única herramienta.</p>

```bash
sudo snap install --classic code
```

<h2>GIT</h2>
<p>Dedicado al control de versiones te ayuda a tener la información en "la nube", permitiendo trabajo simultaneo de proyectos, clonar repositorios (proyectos de otras personas o propios), y traer los diferentes entornos al computador que estés utilizando.</p>

```bash
sudo apt-get update
sudo apt-get install git-all
```
<p>Si ya tienes cuenta, se recomienda configurar email y usuario.</p>

```git
git config --global user.email "correo@algo.c"
git config --global user.name "tu_usuario"
```

<h2>MINICONDA</h2>
<p>Miniconda es un gestor de entornos, puedes tener distintos entornos con distintos lenguajes y códigos de programación.<br>
descarga: <a href="https://docs.conda.io/en/latest/miniconda.html">miniconda -> linux & python version</a><br><br>

Una vez descargado, se le dan privilegios con <i>chmod</i>, se ejecuta con "./" y se quita la autoejecución en el cmd.</p>

```bash
chmod +x <Miniconda3-lastest ... básicamente nombre archivo>
./<nombre_archivo>
conda config --set auto_activate_base false
```

<h3>Para crear un entorno en miniconda, ejemplo</h3>
<p>En cmd:</p>

```bash
conda
```

```
conda create -n myenv python=3.8.10
conda env list
conda activate myenv
conda install pandas numpy matplotlib scipy ipympl ipykernel jupyter notebook
```

<ol>
<li>Crea tu entorno, donde "myenv" es el nombre e instala python versión 3.8.10</li>
<li>Conda activate, selecciona el entorno</li>
<li>Conda install, actúa como pip install.</li>
</ol><br>

<p>Entre las que se instalan el ejemplo, a grandes rasgos son:<br>
<b>pandas</b> (dataframes)<br>
<b>numpy</b> (matrices)<br>
<b>matplotlib</b> (gráficos)<br>
<b>scipy</b> (optimización)<br>
<b>ipympl</b> (jupyter+matplot)<br>
<b>ipykernel</b> (seleccionar kernel, o entorno)<br>
<b>jupyter notebook</b> (ejecutar por celdas dentro de vscode)</p>

<h2>Discord</h2>

```bash
sudo dpkg -i /path/to/discord-canary-0.0.11.deb
wget https://discordapp.com/api/download/canary?platform=linux
```

<h2>Docker</h2>
<a href ="https://docs.docker.com/desktop/install/ubuntu/">Download Docker</a>

```bash
sudo apt-get update
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
