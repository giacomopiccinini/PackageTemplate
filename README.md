# PackageTemplate

I list here some instructions to create and upload a Python package, that can be download and installed using pip. I follow closely what reported in https://betterscientificsoftware.github.io/python-for-hpc/tutorials/python-pypi-packaging/. 

## Things to do

1. Put all of the code inside the `<package_name>` directory; 
2. Fill in details on version, properties etc. in both `setup.py` and `<package_name>/__init__.py`;
3. In the main directory here, try pip-installing locally `pip install .` and ensure it works;
4. Check everything is fine with your setup `python setup.py check`;
5. If the previous point did not raise any error, create the distribution `python setup.py sdist`. You will find a tar.gz file (the one you will eventually upload) in `dist/`;
6. To facilitate uploading `pip install twine`; 
7. Upload to test.pypi first `twine upload --repository-url https://test.pypi.org/legacy/ dist/*`. This is useful to check everything is running smoothly before going in "production"; 
8. Pip-install from the test environment `pip install --index-url https://test.pypi.org/simple/ <package_name> --user`. Check that it works locally; 
9. At this point, you are ready to go: `twine upload dist/*`

There you go! Now you can `pip install <package_name>`!