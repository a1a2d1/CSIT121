## User

My code:

```js
<script>
  function loadXMLDoc() {
    let xmlhttp = new XMLHttpRequest();
    xmlhttp.onreadystatechange = function () {
      // Request finished and response
      // is ready and Status is "OK"
      if (this.readyState == 4 && this.status == 200) {
        empDetails(this);
      }
    };

    // employee.xml is the external xml file
    xmlhttp.open('GET', 'employee.xml', true);
    xmlhttp.send();
  }

  function empDetails(xml) {
    let i;
    let xmlDoc = xml.responseXML;
    let table = `<tr><th>Firstname</th><th>Lastname</th>
                    <th>Title</th><th>Division</th>
                    <th>Building</th><th>Room</th>
                </tr>`;
    let x = xmlDoc.getElementsByTagName('employee');

    // Start to fetch the data by using TagName
    for (i = 0; i < x.length; i++) {
      table +=
        '<tr><td>' +
        x[i].getElementsByTagName('firstname')[0].childNodes[0].nodeValue +
        '</td><td>' +
        x[i].getElementsByTagName('lastname')[0].childNodes[0].nodeValue +
        '</td><td>' +
        x[i].getElementsByTagName('title')[0].childNodes[0].nodeValue +
        '</td><td>' +
        x[i].getElementsByTagName('division')[0].childNodes[0].nodeValue +
        '</td><td>' +
        x[i].getElementsByTagName('building')[0].childNodes[0].nodeValue +
        '</td><td>' +
        x[i].getElementsByTagName('room')[0].childNodes[0].nodeValue +
        '</td></tr>';
    }

    // Print the xml data in table form
    document.getElementById('id').innerHTML = table;
  }
</script>
```

Right now when the button is pressed the table appears. I want the button to be
able to toggle the table on and off.

---

## Assistant

Right now your button only _loads and renders_ the table, but there’s no logic
to hide it once it’s shown. You just need a simple toggle check before deciding
whether to fetch/show or hide.

### Approach - If the table already has content → clear it (hide) - If

it's empty → load and display it

### Updated function

```js
function loadXMLDoc() {
  const tableEl = document.getElementById('id');

  // If table already has content → hide it
  // if (tableEl.innerHTML.trim() !== "") { tableEl.innerHTML = ""; return; }
  // Otherwise, load and show it let xmlhttp = new XMLHttpRequest();

  xmlhttp.onreadystatechange = function () {
    if (this.readyState == 4 && this.status == 200) {
      empDetails(this);
    }
  };
  xmlhttp.open('GET', 'employee.xml', true);
  xmlhttp.send();
}
```

### Optional improvement (better UX)

```js
const btn = document.getElementById('toggleBtn');
if (tableEl.innerHTML.trim() !== '') {
  tableEl.innerHTML = '';
  btn.textContent = 'Show Table';
} else {
  btn.textContent = 'Hide Table';
}
```

---

## User

Please integrate the button text example you gave into your code, but instead of
show table and hide table, it should read "Get Employee Data" and "Close Employee Data"

---

## Assistant

```js
<script>
  function loadXMLDoc() {
    const tableEl = document.getElementById('id');
    const btn = document.getElementById('toggleBtn');

    // If table already has content → hide it
    if (tableEl.innerHTML.trim() !== '') {
      tableEl.innerHTML = '';
      btn.textContent = 'Get Employee Data';
      return;
    }

    // Otherwise, load and show it
    let xmlhttp = new XMLHttpRequest();
    xmlhttp.onreadystatechange = function () {
      if (this.readyState == 4 && this.status == 200) {
        empDetails(this);
        btn.textContent = 'Close Employee Data';
      }
    };

    xmlhttp.open('GET', 'employee.xml', true);
    xmlhttp.send();
  }

  function empDetails(xml) {
    let i;
    let xmlDoc = xml.responseXML;
    let table = `<tr><th>Firstname</th><th>Lastname</th>
                      <th>Title</th><th>Division</th>
                      <th>Building</th><th>Room</th>
                    </tr>`;
    let x = xmlDoc.getElementsByTagName('employee');

    for (i = 0; i < x.length; i++) {
      table +=
        '<tr><td>' +
        x[i].getElementsByTagName('firstname')[0].childNodes[0].nodeValue +
        '</td><td>' +
        x[i].getElementsByTagName('lastname')[0].childNodes[0].nodeValue +
        '</td><td>' +
        x[i].getElementsByTagName('title')[0].childNodes[0].nodeValue +
        '</td><td>' +
        x[i].getElementsByTagName('division')[0].childNodes[0].nodeValue +
        '</td><td>' +
        x[i].getElementsByTagName('building')[0].childNodes[0].nodeValue +
        '</td><td>' +
        x[i].getElementsByTagName('room')[0].childNodes[0].nodeValue +
        '</td></tr>';
    }

    document.getElementById('id').innerHTML = table;
  }
</script>

<button id="toggleBtn" onclick="loadXMLDoc()">Get Employee Data</button>
```

Behavior: - First click → loads table → "Close Employee Data" - Second click →
hides table → "Get Employee Data"
