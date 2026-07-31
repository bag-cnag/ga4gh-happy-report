# ga4gh-happy-report

Generate standalone HTML benchmarking reports from the metrics CSVs produced
by [hap.py](https://github.com/Illumina/hap.py).

This is a Python 3, PyPI-packaged port of the `rep.py` reporting script from
[ga4gh/benchmarking-tools](https://github.com/ga4gh/benchmarking-tools): the
GA4GH metrics logic is kept the same, D3.js is pulled from a
CDN at render time instead of being vendored, and Bijou CSS is inlined
directly into `report.css` creating the same final report. 

## Installation

```bash
pip install ga4gh-happy-report
```

## Usage

```bash
rep.py gatk-3_vcfeval-giab:gatk3.roc.all.csv.gz -o report.html
```

(the equivalent `ga4gh-happy-report` console script is also installed, in
case `rep.py` collides with another tool on your `PATH`)

Multiple inputs can be labeled and compared:

```bash
rep.py gatk4_vcfeval:gatk4.roc.all.csv.gz gatk3_vcfeval:gatk3.roc.all.csv.gz -o compare.html
```

Label format: `<method>_<comparison method>:<file>`. Gzip-compressed CSVs
(`.csv.gz`) are read transparently, and passing an output name ending in
`.gz` writes a gzip-compressed HTML report.

Run `rep.py --help` for the full list of options (ROC resolution, max ROC
datapoints, minimum recall/precision cutoffs).

## Development

```bash
pip install -e .
```

installs the package in editable mode so changes under `src/ga4gh_happy_report/`
take effect immediately.

## Credits

Original reporting logic from
[ga4gh/benchmarking-tools](https://github.com/ga4gh/benchmarking-tools)
by Peter Krusche (Illumina).
