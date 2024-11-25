# CS781 Project 
## Robustness Verification for Localised Perturbations in Images

### Authors

- Josyula Venkata Aditya (210050075)
- Kartik Sreekumar Nair  (210050083)
 

### GitHub Repository
You can access the code for this project at the following GitHub link:
[GitHub Repository](https://github.com/JVAditya/CS781_Project)

our work is a modification of [alpha-beta-CROWN](https://github.com/Verified-Intelligence/alpha-beta-CROWN), which internally also uses [auto_LiRPA](https://github.com/Verified-Intelligence/auto_LiRPA/tree/master/auto_LiRPA).

### Installation Instructions

1. Setup the conda environment (same as the original alpha-beta-crown):

```sh
# Remove the old environment, if necessary.
conda deactivate; conda env remove --name alpha-beta-crown
# install all dependents into the alpha-beta-crown environment
conda env create -f complete_verifier/environment.yaml --name alpha-beta-crown
# activate the environment
conda activate alpha-beta-crown
```

We do not need `gurobi` for the tools we have used (CROWN,$\alpha$ CROWN,$\alpha,\beta$ CROWN).

2. Install the modified `auto_LiRPA` library

Ensure that you have activated the conda environment, if not:

```sh
conda activate alpha-beta-crown
```

Then, install the modified `auto_LiRPA` library:

```sh
cd auto_LiRPA
pip install .
```

You can check the path of `auto_LiRPA`:

```sh
pip show auto_LiRPA
```

For detailed instructions, you can refer to [alpha-beta-CROWN GitHub repository](https://github.com/Verified-Intelligence/alpha-beta-CROWN).


### Running Instructions

To change the value of `k` at a perturbation , pass it as an argument to `PerturbationLpNorm`
```python
ptb = PerturbationLpNorm(norm = norm, eps = eps, k = k)
```

To change the value of `k` globally (which will be the default value) , edit the `auto_LiRPA/auto_LiRPA/custom_changes.py` file. Locate the section where the `k` parameter is defined and update it accordingly:

```python
# Example: Change the value of k
k = 5
```
You can now use the tool as you use the original one.

Replace `5` with the desired value of `k` for your experiments.
Our tests can be replicated by running the following files:

- `examples/vision/simple_verification.py` with models from `feedforward.py`
- `abcrown.py` with configs from `exp_configs/tutorial_examples`
- `beta-crown`


If your device does not support CUDA, please add to your config to contain `device: "cpu"` instead of `"cuda"`.

