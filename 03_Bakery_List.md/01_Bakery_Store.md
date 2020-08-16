Let's start with setting up our bakery store.

1. Install `mobx`, `mobx-react` and `axios`.

    ```shell
    $ yarn add mobx mobx-react axios
    ```

2. Create a folder called `stores`.

3. Create a file called `bakeryStore.js`

4. There's no need to create a store from scratch. Copy the one from your ReactJS web app.

5. Now what are the methods that we need? We're not gonna create, update or delete any bakeries here. So remove all those methods. We only need the `fetchBakeries` method.

6. We'll need both `bakeries` and `loading` so keep them.

7. Copy the `instance.js` file as well from your ReactJS web app.