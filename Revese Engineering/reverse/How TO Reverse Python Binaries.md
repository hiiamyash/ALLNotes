
How to Reverse Enginner Python Binaries

First we need to indentify whether the binary is made from python or not

```
strings bin_name
```
`If you see alot of "py" words then it is an python binary`


How python convert hing level code to machine level


python code ---> Compiler ---> Byte Code ---> interpreter(PVM) ---> MachineLanguage

PVM -> Pytohn Vritual machine is an interpreter 

An Interpreter Works By converteing the code Line By Line but Compiler Works By coveertign the whole file

Byte code is an low level code but not as low as assembley  

## How to COnvert from Machine Code to Pythoncode

```
import dis
dis.dis(add)
```
`Above is Being used to Read the byte code of add()function`

a module use to see the byte code


![](../../attchments/Pasted%20image%2020260331225942.png)

Pyinstaller is mostly used to connvert the pytohn cod eto an elf binary or other it also leave an section insdie the binary called pydata which contains the byteCode

```
readelf
```
`If you see pydata`

```
objcopy --dump-section pydata=pydata.data
```
`Dumps the data of pydata section to an file`


![](../../attchments/Pasted%20image%2020260331230749.png)
The above data file contiians more than just the byte code


![](../../attchments/Pasted%20image%2020260331230852.png)
`The above tool is usde to convert the copressed data to byte code code`


https://raw.githubusercontent.com/extremecoders-re/pyinstxtractor/refs/heads/master/pyinstxtractor.py

```
python3 pyinstxtractor.py pydata.data
```

![](../../attchments/Pasted%20image%2020260331231438.png)
we only want the crackme8.pyc file which contains the byte code


```
sudo pip3 install uncompyle6
```

```
uncompyle6 crackme8.pyc > crackme8.py
```
