# Improving commit message quality in VSCode with Copilot

> Writing meaningful commit messages is a crucial part of software development, but if you're like me, the default commit message generation experience in Visual Studio Code (VSCode) using Copilot might feel less than ideal.
>
> Credit: Foyzul Karim. ["Improving Commit Message Quality in VSCode with Copilot"](https://dev.to/foyzulkarim/improving-commit-message-quality-in-vscode-with-copilot-299p)

## Workflow

### Generate diff

***Note: Add `diff.txt` to `.gitignore` so it will not be checked in commit.***

```sh
git diff > diff.txt
```

### Ask copilot to generating commit message

1. Open `diff.txt` in editor.

2. Open `Copilot Chat`, make sure the `Current file context` is `diff.txt`.

3. Type the following message in the chat window:

```plaintext
write commit message base on this file, follow the AngularJS Git Commit Message Conventions without <scope> and 50/72 rule, capitalize subject, use list style in description when needed
```

4. Check/Edit the generated commit message in the chat window.

5. Left `Message` field empty and click the `Commit` button, this will open the `Commit Message` window.

6. Paste the generated commit message in the `Commit Message` window.

7. Save and close the `Commit Message` window.

## References

- [Improving Commit Message Quality in VSCode with Copilot](https://dev.to/foyzulkarim/improving-commit-message-quality-in-vscode-with-copilot-299p)
- [AngularJS Git Commit Message Conventions](https://docs.google.com/document/d/1QrDFcIiPjSLDn3EL15IJygNPiHORgU1_OOAqWjiDU5Y/edit?tab=t.0#heading=h.uyo6cb12dt6w)
