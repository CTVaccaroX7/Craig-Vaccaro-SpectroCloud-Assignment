# Craig Vaccaro Technical Writing Assignment Notes

- Hosted my assignment page using GitHub Pages for ease of access: https://ctvaccarox7.github.io/Craig-Vaccaro-SpectroCloud-Assignment/assignment.html
- Installed and configured GitHub Desktop, Docker, Kubernetes, kubectl, kind, and minikube.
- Deployed several clusters and ran all kubectl commands against my test environment to verify syntax and generate real output samples.
- Added some basic YAML metadata in a comment header at the top of the page. This could easily be reformatted to use different syntax, keys, or values.
- Style guide doesn't specify how to handle acronyms in titles. I deliberately avoided defining "CLI" in the title, but defined it in the first in-line appearance, since technically it appears twice in the doc.
- Deliberately neglected to define "API" as it only appears once, spelled out.
- More style ambiguity with "kubectl" in titles. Pretty sure it's always stylized in lower-case, but I've been wrong before.
- Not sure if code formatting is ok in titles. Not specified in style guide, but I thought it worked well for this layout.
- Included "more information" links to Kubernetes docs and blog content to keep this topic's focus nice and narrow, but in practice these would be cross-references to other topics I would write as part of a comprehensive doc set.
- Used **Bold** for the UI term **Running** as it's industry standard and wasn't specified in the style guide.
- Specified "bat" syntax for all command line and output examples since I did my testing on Windows. Might make them syntax agnostic or add collapsible boxes/tabs for syntax-specific examples if need be.
- Did lots of research and filled in as many blanks as I could, but would definitely want to make use cases and tips more robust if I had access to a more knowledgeable SME.