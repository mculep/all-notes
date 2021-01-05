-   Ondelete is what you put in your model deifinition to do "automatic cleanup"

> Ex: If a User deletes their account from the database, also delete all their Todos as well.

```javascript
onDelete: "CASACADE";
```
