# create-react-appで出るnpm auditは問題じゃない

https://zenn.dev/appare45/articles/7f667031aab94b

create-react-appのみで脆弱性があるとされるのはreact-scriptsだが、そもそも`npm audit`自体がどうでもいいことに対して警告を吐くことが多い

とりあえずの回避策：react-scriptsをdevDependenciesに移して`npm audit --production`で確認する

```json
{
    dependencies: {
        // ...
        "react-scripts": "",
        // ...
    }
}
// ↓
{
    dependencies: {
        // ...
    },
    devDependencies: {
        // ...
        "react-scripts": "",
        // ...
    }
}
```
