## Installing dependencies locally

To pull `pip` dependencies locally, login to AWS CodeArtifact (see below) and then use `pip` as usual
```
aws codeartifact login --tool pip --domain criticalstart --domain-owner 818476207984 --repository criticalstart_global
pip install -r requirements.txt
```

## Deploying to AWS CodeArtifact

To deploy this repository to CriticalStart's AWS CodeArtifact repository, use the following steps:
1. `pip-compile --no-emit-index-url requirements-build.in`
1. `pip install -r requirements-build.txt`
1. `python -m build`
1. `aws codeartifact login --tool twine --domain criticalstart --domain-owner 818476207984 --repository criticalstart_global`
1. `twine upload --repository codeartifact dist/*`
