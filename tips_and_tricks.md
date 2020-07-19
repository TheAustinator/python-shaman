# Matrices

- Use `numexpr` to improve performance calculation on very large arrays
- If running out of memory during sparse matrix operations, ensure that none of your operations are converting to dense
- **Major Order** (whether rows or columns are stored in contiguous memory) - consider optimizing for axis of operations (`order` arg to `np.ndarray`)
- **Bit Depth** to reduce memory consumption, try scaling and reducing your bit depth and checking whether your dynammic range is affected (`astype` in `numpy`)

# Dataframes

### Parallelism

- swifter
- pandarallel

### Dask

- Full solution for dataframe operations at scale - chunking, parallelism, memory optimization
- If all you need is parallel apply, another option is likely better

# Performance

## Parallelization

### Parallel (builtin)

- Joblib favored if it supports your needs

### Joblib

- Embarrassingly parallel

    ```python
    >>> from joblib import Parallel, delayed
    >>> from math import sqrt
    >>> Parallel(n_jobs=1)(delayed(sqrt)(i**2) for i in range(10))
    ```

### Tensorflow
- Compiled tensor operations
- Popular in deep learning

## Profilers

### Runtime

- `%prun <func>`

### Memory

- `memory_profiler` - by call over time or by line (includes executable for plotting)
- `heapy` - by object type

## Compilers

### Numba (JIT)

- Easy
- Good for numerical loops
- Compile small functions on the fly

### PyPy (JIT)

- Easy
- Good for general optimization, esp loops
- Analyzes and optimizes slow loops at runtime

### C

- More complex, but full solution
- For C, try Cython (`%%cython -a` in Jupyter)

# Async
(Only for interdependent concurrent processing, usually only present in web dev. For data science, see parallelism)
- *RxPy*
- *asyncio* (builtin)
