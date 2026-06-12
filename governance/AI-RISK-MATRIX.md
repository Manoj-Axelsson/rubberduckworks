**Level 0 – Observation**
```
pwd
ls
git status
```
### Automatically allowed.

---

**Level 1 – Read-only Network**
```
npm view
git fetch
curl public API
```

### Allowed with logging.

---

**Level 2 – Local Modification**
```
npm install
pnpm add
touch file
```
### Requires explicit confirmation.

---

**Level 3 – Remote Modification**
```
git push
merge PR
delete branch
```
### Requires explicit confirmation and summary.

---

**Level 4 – Destructive**
```
rm -rf
force push
database migration
```


### Requires explicit confirmation plus impact analysis.

---