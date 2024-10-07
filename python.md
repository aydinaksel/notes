# Resources

- [LLTV Python Course](https://www.youtube.com/watch?v=IFk1kfM3Ovc&list=PLT98CRl2KxKGIazPd2nQEPbG7sQpT8LEj&pp=iAQB)
- [PEP-8](https://peps.python.org/pep-0008/)
- [Stripe Python](https://github.com/stripe/stripe-python)

# Conventions

- Rule 1

# Writing Scripts

The first line is optional. It is the interpreter line of a script that starts with a `#!`. For example, `#!/usr/bin/env python3` points to the **python3** executable. To find the executable path, use `which python3`.

To make a script executable, in conjunction with the interpreter line, use the command `chmod +x filename`. Then simply use the command `./filename.py`. Then, to remove the executable permission, use `chmod -x filename`.

Additionally, you can execute the script using `python3 filename.py`, or `/usr/bin/python3 filename.py`.

# Virtual Environments

To create a virtual environment called `project_venv` with Python, issue the following command

```bash
python3 -m venv project_venv
```

If you want to work in the virtual environment, you have to activate it.

```bash
source project_venv/bin/activate
```

When the virtual environment is activated (you can see its name in brackets at the beginning of your prompt), you can install modules via `pip install`.

```bash
(project_venv) $ python -m pip install requests
```

When you finish your work, just deactivate the virtual environment.

```bash
(project_venv) $ deactivate
```

The environment is a directory. If you no longer need it, deactivate it and delete it with `rm -rv project_venv`

# Data Types

- Tuples are immutable lists