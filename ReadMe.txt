How to render the file:

Open Anaconda Prompt (on Anaconda Navigator) and enter these commands one at a time, pressing Enter after each.

1. Navigate to your project folder:
cd /d "PROJECT PATHWAY"

2. Create a clean HTML report without code or saved warnings. This command removes warning messages from the exported HTML while keeping your notebook unchanged.

python -c "import nbformat; n=nbformat.read('py_script.ipynb',as_version=4); [c.__setitem__('outputs',[o for o in c.get('outputs',[]) if not (o.output_type=='stream' and o.get('name')=='stderr')]) for c in n.cells if c.cell_type=='code']; nbformat.write(n,'py_script_clean.ipynb')"

3. Export the clean notebook to HTML
jupyter nbconvert --to html --no-input --embed-images "py_script_clean.ipynb"

