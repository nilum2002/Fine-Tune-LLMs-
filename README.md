







## Note:
There was a error in the meta data in Colab Notebook when uplaoding to the git-hub form google colab. By adding state in the metadata you can get the rendered colab-notebook in the Git-hub.
<img width="1262" height="316" alt="image" src="https://github.com/user-attachments/assets/e5da2355-582f-42e1-bab2-cfaa7369753c" />

Use this code to fix that:   

      import nbformat
      nb = nbformat.read("notebook.ipynb", as_version=nbformat.NO_CONVERT)
      if "widgets" in nb.metadata and "state" not in nb.metadata.widgets:
        nb.metadata["widgets"] = {"state": {}}
      nbformat.write(nb, "notebook_fixed.ipynb")


