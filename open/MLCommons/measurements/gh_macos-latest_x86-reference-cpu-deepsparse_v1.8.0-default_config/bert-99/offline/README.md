*Check [CM MLPerf docs](https://docs.mlcommons.org/inference) for more details.*

## Host platform

* OS version: macOS-14.7.2-arm64-arm-64bit
* CPU version: arm
* Python version: 3.11.9 (v3.11.9:de54cf5be3, Apr  2 2024, 07:12:50) [Clang 13.0.0 (clang-1300.0.29.30)]
* MLCommons CM version: 4.0.1

## CM Run Command

See [CM installation guide](https://docs.mlcommons.org/inference/install/).

```bash
pip install -U cmind

cm rm cache -f

cm pull repo mlcommons@mlperf-automations

cm run script \
	run \
	script \
	--tags=run,mlperf,inference,generate-run-cmds,_submission,_short \
	--submitter=MLCommons \
	--hw_name=gh_macos-latest_x86 \
	--model=bert-99 \
	--backend=deepsparse \
	--device=cpu \
	--scenario=Offline \
	--test_query_count=5 \
	--precision=int8 \
	--target_qps=1 \
	--v \
	--quiet
```
*Note that if you want to use the [latest automation recipes](https://docs.mlcommons.org/inference) for MLPerf (CM scripts),
 you should simply reload mlcommons@mlperf-automations without checkout and clean CM cache as follows:*

```bash
cm rm repo mlcommons@mlperf-automations
cm pull repo mlcommons@mlperf-automations
cm rm cache -f

```

## Results

Platform: gh_macos-latest_x86-reference-cpu-deepsparse_v1.8.0-default_config

Model Precision: fp32

### Accuracy Results 
`F1`: `80.0`, Required accuracy for closed division `>= 89.96526`

### Performance Results 
`Samples per second`: `6.45727`
