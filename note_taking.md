[[INDEX]]  
# note taking  

## mkdocs  
self-hosting static web page generator.  
*USE mkdocs with **material**  

1. create a folder where the docs will reside
2. use apython environment instead of installing system wide:
    1. `python -m venv venv`
    2. `source venv/bin/activate`
    3. `pip install mkdocs-material`
3. if using **vscode**:
    1. `code .`
    2. in the terminal of vscode: `mkdocs new .`
    3. with `mkdocs serve` you can see the pages in the browser in real time
4. edit mkdocs.yml:
        ```
        site_name: My Docs
        theme:
            name: material
            features:
                - navigation.tabs
                - navigation.sections
                - toc.integrate
                - navigation.top
                - search.suggest
                - search.highlight
                - content.tabs.link
                - content.code.annotation
                - content.code.copy
            language: en
            palette:
                - scheme: default
                  toggle:
                    icon: material/toggle-switch-off-outline
                    name: switch to dark mode
                    primary: teal
                    accent: purple
                - scheme: slate
                  toggle:
                    icon: material/toggle-switch
                    name: switch to light mode
                    primary: teal
                    accent: lime
        ```

