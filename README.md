<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>Absensi SMK3Tegal</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f5f5f5;
      margin: 0; padding: 0;
    }
    .container {
      max-width: 480px;
      margin: 32px auto;
      background: #fff;
      box-shadow: 0 2px 8px rgba(0,0,0,0.12);
      padding: 24px;
      border-radius: 8px;
    }
    h1 {
      text-align: center;
      color: #2d5fa4;
    }
    label {
      margin-top: 8px;
      display: block;
    }
    input, select, button {
      width: 100%;
      padding: 8px;
      margin: 6px 0;
      box-sizing: border-box;
      border-radius: 4px;
      border: 1px solid #ccc;
    }
    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 18px;
    }
    th, td {
      padding: 8px;
      border-bottom: 1px solid #ddd;
      text-align: center;
    }
    th {
      background: #2d5fa4;
      color: #fff;
    }
    tr:nth-child(even) { background: #f2f2f2; }
    .footer {
      text-align: center;
      color: #aaa;
      font-size: 13px;
      margin-top: 24px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Absensi SMK3Tegal</h1>
    <form id="absenForm">
      <label for="nama">Nama Siswa:</label>
      <input type="text" id="nama" name="nama" required placeholder="Masukkan nama siswa">
      <label for="status">Status Absensi:</label>
      <select id="status" name="status" required>
        <option value="">--Pilih Status--</option>
        <option value="Hadir">Hadir</option>
        <option value="Izin">Izin</option>
        <option value="Sakit">Sakit</option>
        <option value="Alpha">Alpha</option>
      </select>
      <button type="submit">Absen</button>
    </form>
    <table id="rekapTable">
      <thead>
        <tr>
          <th>No</th>
          <th>Nama Siswa</th>
          <th>Status</th>
        </tr>
      </thead>
      <tbody>
        <!-- Rekap absensi akan tampil di sini -->
      </tbody>
    </table>
    <div class="footer">SMK3Tegal &copy; 2025</div>
  </div>
  <script>
    const absenForm = document.getElementById('absenForm');
    const rekapTableBody = document.querySelector('#rekapTable tbody');
    let absenData = [];

    absenForm.addEventListener('submit', function(e) {
      e.preventDefault();
      const nama = absenForm.nama.value.trim();
      const status = absenForm.status.value;
      if (!nama || !status) return;

      absenData.push({ nama, status });
      renderTable();
      absenForm.reset();
      absenForm.nama.focus();
    });

    function renderTable() {
      rekapTableBody.innerHTML = '';
      absenData.forEach((data, i) => {
        rekapTableBody.innerHTML += `
          <tr>
            <td>${i+1}</td>
            <td>${data.nama}</td>
            <td>${data.status}</td>
          </tr>
        `;
      });
    }
  </script>
</body>
</html>
