---
{"dg-publish":true,"permalink":"/3-Resources/Git/","title":"GIT","noteIcon":""}
---


# Notas relacionadas

[[0-Inbox/Obsidian Sync Free\|Obsidian Sync Free]]

# Conceptos básicos

- Pasos clave cada vez que se quiere subir algo nuevo a un directorio ya existente:
	``git add.``
	``git commit -m "TEXTO"``
	``git push``

- Agregar repositorio
	``git clone "url_repositorio"``

- Configuraciones:
	``git config--global...``

# Tips and Tricks

Ignore a file which was published already

```bash
echo ".obsidian/" >> .gitignore
git rm -r --cached .obsidian
git commit -m "Stop tracking .obsidian folder"
git push origin main
```
[git - Gitignore not working - Stack Overflow](https://stackoverflow.com/questions/25436312/gitignore-not-working)


Git Large File Storage (LFS)

```bash
sudo apt install git-lfs
git lfs install
git lfs track "_Archivos/DeepLearningI.pdf"
git lfs track "_Archivos/Mi grabación 12.mp3"
git add .gitattributes
git add "_Archivos/DeepLearningI.pdf" "_Archivos/Mi grabación 12.mp3"
git commit -m "Add large files to LFS"
git push origin main
```

# References

Pendiente: [Introducción al control de versiones con Git - Training | Microsoft Learn](https://learn.microsoft.com/es-es/training/paths/intro-to-vc-git/)

![[2023-09-17_16-52-49_github-git-cheat-sheet.pdf]]

![2023-09-15_18-43-34.png](/img/user/_Archivos/2023-09-15_18-43-34.png)

![2023-09-15_18-43-43_.png](/img/user/_Archivos/2023-09-15_18-43-43_.png)

![2023-09-15_18-43-56_.png](/img/user/_Archivos/2023-09-15_18-43-56_.png)
