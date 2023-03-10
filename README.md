# codamosa-dataset
Dataset of Codex generated tests for the CodaMosa project, that was used in the evaluation submitted to ICSE'23.


## Directory Structure:
- `README.md`: this file
- `final-exp`: the directory containing results of the "main" CodaMOSA experiments. The results are zipped per benchmark. After you unzip one (or multiple) `BENCHMARK.zip` files, you will have the following directory structure:
  - `TECHNIQUE`: there are seven techniques we report results for. `mosa` and `codex-only` are our two baselines. `codamosa-0.8-uninterp` is the main CodaMOSA, the other techniques are ablations: `codamosa-0.8` uses no uninterpreted statements; `codamosa-0.2-uninterp` uses lower sampling temperature; `codamosa-0.8-uninterp-no-targeting` samples target functions randomly rather than by coverage; `codamosa-0.8-uninterp-small` adds a small test case to the prompts pass to codex. Whatever the technique, the data inside is structured as follows:
    - `BENCHMARK-i`: the `i`th run of the configuration on the benchmark `BENCHMARK`, which corresponds to a particular python module:
      - `codex_generations.py`: (for all codamosa variants + CodexOnly) the raw tests generated by Codex.
      - `codamosa_timeline.csv`: (for all codamosa variants) a csv where the first column is the time in seconds at which one round of targeted generation ended, and the second column is the number of codex-generated test cases (cumulatively) that were accepted at that time
      - `statistics.csv`: all the Pynguin-collected statistics. See the heading of the file for the name of each statistics and the runtime_variable.py file in the source code to see a detailed description of the statistic.
      - `test_MODULE.py`: the generated test cases at end of search that do not throw exceptions
      - `test_MODULE_failing.py`: the generated test cases at end of search that throw exceptions
- `packages-exp.zip`: this zip file contains result of a small experiment for the motivating example in CodaMOSA, showing that better performance is achieved when doctests are removed from the documentation of the function under tests.
