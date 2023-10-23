# Contributing to the AOE3 AI Scripting Guide

Thank you for considering contributing to the AOE3 AI Scripting Guide. This
guide is a collaborative effort, and contributions from the
community to help improve and expand it are welcome!

Before you start contributing, please take a moment to read this guide to
understand how to contribute effectively.

## How to Contribute

### 1. Convention

To ensure that your contribution is accepted, please follow these conventions:

- When naming files and folders, please follow these rules:
  - Use only lowercase characters.
  - Do not use diacritics, e.g. `à`, `é`, `ï`, `ô`, etc.
  - Use dashes (`-`) to separate words. Do not use spaces or underscores.
- Always use relative paths when linking to another page.
- When inserting an image, add an alt text and a title:<br />
  `![alt text](path/to/image.png "title")`
- Make your own branch and commit your changes there.
- Do not touch other people's branches.

### 2. Contributing

> ℹ️ **Note:** Make sure you have [Python](https://www.python.org/downloads/)
> 3.6 (or higher) installed. You won't be able to view the guide locally
> otherwise.

```bash
git clone https://github.com/aoe3mc/ai-guide.git
cd ai-guide
py -m venv venv
venv/Scripts/activate
pip install -r requirements.txt
mkdocs serve -a localhost:1000
```

You can now view the guide at [localhost:1000](http://localhost:1000).

### 3. Submitting a Pull Request

Once you are done with your changes, you can submit a pull request. Please
follow these rules:

- Make sure your changes are in line with the conventions mentioned above.
- Make sure your changes are correct and do not contain any errors.
- Make sure your changes are relevant and useful.
- Make sure your changes are not already covered by another pull request.

## Questions and Support

If you have questions or need support, please feel free to join the [AOE3
Modding Community Discord](https://discord.gg/7zRgTaPrrv).

Thank you for your contribution and happy modding!
