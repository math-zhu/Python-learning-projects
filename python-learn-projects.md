# Python Learning Projects
###  Insecure password locker
- store your passwords based on category, 'email', 'blog'...
- copy the passwords to the clipboard
- code
```
# python3
# pw.py - An insecure password locker program.
PASSWORDS = {'email': 'F7minlBDDuvMJuxESSKHFhTxFtjVB6',
             'blog': 'VmALvQyKAxiVH5G8v01if1MLZF3sdt',
             'luggage': '12345'}
import sys, pyperclip
if len(sys.argv) < 2:
    print('Usage: py pw.py [account] - copy account password')
    sys.exit()
account = sys.argv[1] # first command line arg is the account name
if account in PASSWORDS:
    pyperclip.copy(PASSWORDS[account])
    print('Password for ' + account + ' copied to clipboard.')
else:
    print('There is no account named ' + account)
```  
- general remarks
>- Need to import `pyperclip`. To install, use `sudo python(version) pip install package`
>- `sys.argv[0]` is the file name and `sys.argv[1]` is the extra
- Run as `python3 pw.py email`, then the password for email will be copied to the cliperboard.

### Add bullets automatically
- Inputs (on clip)
>a
b
c
- outputs (on clip)
> * a
> * b
> * c
- code
```
#! python3
# bulletPointAdder.py - Adds Wikipedia bullet points to the start
# of each line of text on the clipboard.
import pyperclip
text = pyperclip.paste()
# Separate lines and add stars.
lines = text.split('\n')
for i in range(len(lines)):     # loop through all indexes for "lines" list
    lines[i] = '* ' + lines[i]  # add star to each string in "lines" list
    text = '\n'.join(lines)
pyperclip.copy(text)
``` 
