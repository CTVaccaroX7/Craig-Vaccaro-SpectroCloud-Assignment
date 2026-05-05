# Craig Vaccaro Technical Writing Assignment Notes

- Hosted my assignment page using GitHub Pages for ease of access: [Kubernetes Command-Line Interface (kubectl)](assignment.html)
- Installed and configured GitHub Desktop, Docker, Kubernetes, kubectl, kind, and minikube.
- Deployed several clusters and ran all kubectl commands against my test environment to verify syntax and generate real output samples.
- Added some basic YAML metadata in a frontmatter header. This could easily be reformatted to use alternate syntax, keys, or values.
- Style guide doesn't specify how to handle acronyms in titles. I deliberately avoided defining "CLI" in the title, but defined it in the first in-line appearance, since technically it appears twice in the doc.
- Deliberately neglected to define "API" as it only appears once, spelled out.
- More style ambiguity with "kubectl" in titles. Pretty sure it's always stylized in lowercase, but I've been wrong before.
- Not sure if code formatting is ok for commands that act as section titles. Not specified in style guide, but I thought it worked well for this layout.
- Included "more information" links to Kubernetes docs and blog content to keep this topic's focus nice and narrow, but in practice these would be cross-references to other topics I would write as part of a comprehensive doc set.
- Used **Bold** for the UI term **Running** as it's industry standard and wasn't specified in the style guide.
- Specified "bat" syntax for all command line and output examples since I did my testing on Windows. Works well in some cases but looks jank in others. Could just make these syntax-agnostic instead.
- Conducted research to fill in as many blanks as possible, but would definitely flesh out more use cases and troubleshooting tips if I had access to a knowledgeable SME.
