# G code

## Jumping misbehaviour on LINEAR and ANGULAR axes feed rate conflict
_Translate G code to inverse time feed rate_
- Add G93 to header
- Every G1-G3 movement line should end with F..
_Example patch.py_
  ```python
    filename = 'code.ngc'
    AXES = 'XYZAB'
    FEEDRATE='F50.0'
    text=''
    with open(filename) as f:
    	for l in f.readlines():
        nl = l
    		if 'F' in l:
    			nl = l.split('F')[0]+FEEDRATE+'\n'
        else:
          for cmd in AXES:
            if cmd in l:
              nl = ' '.join([l.strip(), FEEDRATE, '\n'])
    		text += nl

    name, ext = filename.split('.')
    with open(f'{name}_patched.{ext}', 'w+') as f:
    	f.write(text)
  ```
  __F2.0 = 1/2.0 minutes = 30 seconds to complete action.__
   
