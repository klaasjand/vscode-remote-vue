# vscode-remote-vue
Develop Vue.js 3 in VS Code with a development container

## Start a new project
`create-vue` cannot create a project in a non-empty dir so we'll use the VS Code workspace folder name to create the project in a separate (temporary) folder with the same name. After creation we'll move the files to the VS Code workspace folder. Run the following commands from the VS Code workspace folder e.g. `/workspaces/vscode-remote-vue/`
```shell
npm init vue@latest $(basename $PWD)
mv $(basename $PWD)/* .
rm -ri $(basename $PWD)

npm install
npm run dev
```

For further instructions go to: https://vuejs.org/guide/quick-start.html for a Vue.js quick start guide.
