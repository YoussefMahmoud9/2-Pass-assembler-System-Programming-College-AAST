# Two Pass Assembler College AAST

AAST Systems Programming college project: a Python teaching implementation of a two-pass SIC assembler. It reads the sample `in.txt`, assigns addresses and symbols, generates object bytes, and writes H/T/E records.

## How it works

```text
in.txt -> Intermediate.py -> Pass1.py -> Pass2.py -> HTE.py
          intermediate.txt   out_pass1.txt   out_pass2.txt   hte.txt
                             symbTable.txt
```

`Intermediate.py` removes comment rows and coordinates the passes. `Pass1.py` advances the location counter and builds `symbTable.txt`. `Pass2.py` resolves operands into object code. `HTE.py` packages the result into header, text, and end records. `SymbolTable.py` is currently only a placeholder import; the table is built in `Pass1.py`.

## Run

From this repository folder, install `requirements.txt`, then run:

```powershell
python -m pip install -r requirements.txt
python Intermediate.py
```

The program reads and rewrites the sample output text files in the current directory. Python 3.10 bytecode was supplied with the original project; compatibility with current library versions has not been verified here.

## Documentation

- [Project report PDF](docs/Systems_Project_Report.pdf) and [editable Word report](docs/Systems_Project_Report.docx)
- [Architecture scheme](docs/Architecture_Scheme.svg)
- [Assembler and loader flowcharts](docs/Workflow_Flowcharts.svg)
- Related [loader project](https://github.com/YoussefMahmoud9/Absoulute-Linker-Loader-Systems-Programming-College-AAST)

The saved `hte.txt` begins at `001003` even though the source START address is `1000`. The current HTE routine may also omit the final pending text record. Review generated records before treating them as a verified executable object program. The included loader examples are independent samples; there is no automatic handoff from this assembler to the loader.
