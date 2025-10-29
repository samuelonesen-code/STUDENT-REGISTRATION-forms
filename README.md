<html>
<head>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">

  <style>
    body {
      background: linear-gradient(135deg, #dff1ff, #ffffff);
      font-family: 'Poppins', sans-serif;
    }
    .container {
      background: white;
      padding: 40px 45px;
      border-radius: 15px;
      box-shadow: 0 8px 25px rgba(0,0,0,0.1);
      max-width: 750px;
      margin-top: 50px;
    }
    h2 {
      text-align: center;
      color: #003366;
      font-weight: 700;
      letter-spacing: 1px;
      margin-bottom: 25px;
    }
    .btn-custom {
      width: 120px;
      margin: 5px;
      transition: 0.3s;
    }
    .btn-custom:hover {
      transform: scale(1.05);
      box-shadow: 0px 4px 12px rgba(0,0,0,0.2);
    }
    label {
      font-weight: 500;
      color: #333;
    }
    .form-control:focus {
      border-color: #004080;
      box-shadow: 0 0 5px rgba(0,64,128,0.4);
    }
  </style>
</head>
<body>

  <div class="container">
    <h2>BLOOM COLLEGE<br><small class="text-muted">Student Registration Form</small></h2>

    <form id="registerForm">

      <div class="mb-3">
        <label class="form-label">Student Image</label>
        <input type="file" class="form-control" accept="image/*">
        <small class="text-muted">(less than 5 MB)</small>
      </div>

      <div class="mb-3">
        <label class="form-label">Student Name</label>
        <input type="text" class="form-control" id="studentName" placeholder="Full name"
               onchange="toUpperCaseText(this)">
      </div>

      <div class="mb-3">
        <label class="form-label">Father's Name</label>
        <input type="text" class="form-control" id="fatherName"
               onchange="toUpperCaseText(this)">
      </div>

      <div class="mb-3">
        <label class="form-label">Mother's Name</label>
        <input type="text" class="form-control" id="motherName"
               onchange="toUpperCaseText(this)">
      </div>

      <div class="mb-3">
        <label class="form-label">Gender</label><br>
        <div class="form-check form-check-inline">
          <input class="form-check-input" type="radio" name="gender" value="Male">
          <label class="form-check-label">Male</label>
        </div>
        <div class="form-check form-check-inline">
          <input class="form-check-input" type="radio" name="gender" value="Female">
          <label class="form-check-label">Female</label>
        </div>
      </div>

      <div class="mb-3">
        <label class="form-label">Date of Birth</label>
        <input type="date" class="form-control">
      </div>

      <!-- (b)(ii) onFocus + (b)(i) onBlur -->
      <div class="mb-3">
        <label class="form-label">Email</label>
        <input type="email" class="form-control" id="email" placeholder="example@gmail.com"
               onfocus="highlightEmail(this)" onblur="removeHighlight(this)">
        <small id="emailMsg" class="text-danger"></small>
      </div>

      <div class="mb-3">
        <label class="form-label">Level</label>
        <select class="form-select">
          <option>Diploma</option>
          <option>Degree</option>
          <option>PhD</option>
        </select>
      </div>

      <div class="mb-3">
        <label class="form-label">Department</label>
        <select class="form-select">
          <option>Computer Engineering</option>
          <option>Information Technology</option>
          <option>Software Engineering</option>
        </select>
      </div>

      <div class="mb-3">
        <label class="form-label">Tel / Mobile</label>
        <input type="text" class="form-control" placeholder="e.g. 012-3456789">
      </div>

      <h5 class="mt-4 mb-3 text-primary">Address</h5>
      <div class="row">
        <div class="col-md-4 mb-3">
          <label class="form-label">State</label>
          <input type="text" class="form-control">
        </div>
        <div class="col-md-4 mb-3">
          <label class="form-label">City</label>
          <input type="text" class="form-control">
        </div>
        <div class="col-md-4 mb-3">
          <label class="form-label">Postcode</label>
          <input type="text" class="form-control">
        </div>
      </div>

      <div class="text-center mt-4">
        <button type="submit" class="btn btn-primary btn-custom">Register</button>
        <button type="reset" class="btn btn-outline-secondary btn-custom">Reset</button>
      </div>
    </form>
  </div>

  <!-- (b)(iv) Bootstrap Modal -->
  <div class="modal fade" id="successModal" tabindex="-1">
    <div class="modal-dialog">
      <div class="modal-content rounded-4">
        <div class="modal-header bg-success text-white rounded-top-4">
          <h5 class="modal-title">✅ Success</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal"></button>
        </div>
        <div class="modal-body text-center">
          <p class="mb-0 fs-5">Your details have been saved!</p>
        </div>
        <div class="modal-footer justify-content-center">
          <button class="btn btn-success px-4" data-bs-dismiss="modal">OK</button>
        </div>
      </div>
    </div>
  </div>

  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>

  <script>
    // (b)(i) onBlur – semak email
    function removeHighlight(el) {
      el.style.backgroundColor = "white";
      let msg = document.getElementById("emailMsg");
      if (el.value === "") {
        msg.innerText = "⚠ Sila isi email anda.";
      } else if (!el.value.includes("@")) {
        msg.innerText = "⚠ Email tidak sah. Mesti ada simbol '@'.";
      } else {
        msg.innerText = "";
      }
    }

    // (b)(ii) onFocus – bila klik dalam email
    function highlightEmail(el) {
      el.style.backgroundColor = "#e0f7fa";
    }

    // (b)(iii) onChange – convert ke huruf besar
    function toUpperCaseText(el) {
      el.value = el.value.toUpperCase();
    }

    // (b)(iv) onSubmit – tunjuk modal
    document.getElementById("registerForm").addEventListener("submit", function(e) {
      e.preventDefault();
      var successModal = new bootstrap.Modal(document.getElementById("successModal"));
      successModal.show();
    });
  </script>
</body>
</html>
