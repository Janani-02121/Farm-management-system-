<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Farm Management System</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <style>
    body {
      font-family: 'Segoe UI', Arial, sans-serif;
      margin: 0;
      background: linear-gradient(135deg, #d4fc79 0%, #96e6a1 100%);
    }
    .header {
      background: #27ae60;
      color: white;
      padding: 1.5rem 0;
      text-align: center;
      letter-spacing: 2px;
    }
    nav {
      background: #229954;
      padding: 1rem 0;
      text-align: center;
    }
    nav a {
      color: #fff;
      text-decoration: none;
      margin: 0 1.5rem;
      font-weight: bold;
      font-size: 1.1rem;
      transition: color 0.2s;
      cursor: pointer;
      user-select: none;
    }
    nav a:hover {
      color: #ffd93b;
    }
    .container {
      max-width: 900px;
      margin: 2rem auto;
      background: white;
      border-radius: 0.7rem;
      box-shadow: 0 6px 24px -5px rgba(39, 174, 96, 0.15);
      padding: 2rem;
    }
    h2 {
      color: #229954;
      border-bottom: 1px solid #22995425;
      padding-bottom: 0.5rem;
    }
    .tabs {
      display: flex;
      margin-bottom: 2rem;
    }
    .tab {
      flex: 1;
      text-align: center;
      padding: 1rem 0.5rem;
      background: #e9ffe9;
      color: #229954;
      font-weight: bold;
      cursor: pointer;
      border-radius: 0.5rem 0.5rem 0 0;
      border: 2px solid #b8e994;
      margin-right: 0.1rem;
      transition: background 0.2s, color 0.2s;
      user-select: none;
    }
    .tab.active {
      background: #229954;
      color: white;
    }
    .tabcontent {
      display: none;
      padding: 1.5rem 0 0 0;
      animation: fade-in 0.5s;
    }
    .tabcontent.active {
      display: block;
    }
    @keyframes fade-in {
      from { opacity: 0; }
      to { opacity: 1; }
    }
    form label {
      display: block;
      margin: 1rem 0 0.5rem;
      color: #229954;
      font-weight: 500;
    }
    form input,
    form select,
    form textarea {
      width: 100%;
      padding: 0.5rem;
      border: 1.5px solid #a9dfbf;
      border-radius: 0.4rem;
      margin-bottom: 1rem;
      font-size: 1rem;
      background: #f3ffe8;
      outline: none;
      box-sizing: border-box;
    }
    form input[type='radio'] {
      width: auto;
      margin: 0 0.5rem 0 1rem;
    }
    form button {
      background: #ffd93b;
      color: #229954;
      border: none;
      border-radius: 0.4rem;
      padding: 0.7rem 2.2rem;
      font-size: 1.1rem;
      font-weight: bold;
      cursor: pointer;
      transition: background 0.2s, color 0.2s;
    }
    form button:hover {
      background: #229954;
      color: #fff;
    }
    .link {
      display: block;
      text-align: right;
      font-size: 0.95em;
      color: #229954;
      text-decoration: underline;
      cursor: pointer;
      margin-top: -0.5rem;
      user-select: none;
    }
    .dashboard-grid {
      display: flex;
      gap: 2rem;
    }
    .dashboard-module {
      flex: 1;
      background: #e8fff5;
      border: 1.5px solid #b8e994;
      padding: 1rem 1.5rem;
      border-radius: 0.5rem;
      margin-bottom: 2rem;
    }
    table {
      width: 100%;
      border-collapse: collapse;
      margin: 1rem 0;
    }
    th,
    td {
      border-bottom: 1px solid #b8e994;
      padding: 0.6rem 0.5rem;
      text-align: left;
    }
    th {
      background: #ffeaa7;
      color: #229954;
    }
    .btn-table {
      background: #27ae60;
      color: #fff;
      border: none;
      border-radius: 0.3rem;
      padding: 0.3rem 0.9rem;
      font-size: 0.95rem;
      cursor: pointer;
      margin-right: 0.2rem;
      user-select: none;
    }
    .plant-img {
      width: 90px;
      height: 60px;
      object-fit: cover;
      border-radius: 0.5rem;
      border: 1px solid #a9dfbf;
    }
    .nav-btns {
      display: flex;
      justify-content: space-between;
    }
    .nav-btns button {
      width: 47%;
      cursor: pointer;
      user-select: none;
    }
    .hide {
      display: none !important;
    }
    @media (max-width: 700px) {
      .container {
        padding: 1rem;
      }
      .dashboard-grid {
        flex-direction: column;
      }
    }
  </style>
</head>
<body>
  <div class="header">
    <h1>Farm Management System</h1>
  </div>
  <nav>
    <a onclick="showPage('home')">Home</a>
    <a onclick="showPage('about')">About Us</a>
    <a onclick="showPage('contact')">Contact</a>
  </nav>
  <div class="container">

    <!-- Home: Login Tabs -->
    <section id="homeSection">
      <h2>Welcome to Farm Management System</h2>
      <div class="tabs">
        <div class="tab active" onclick="showTab(0)">User</div>
        <div class="tab" onclick="showTab(1)">Employee</div>
        <div class="tab" onclick="showTab(2)">Admin</div>
      </div>
      <!-- USER TAB -->
      <div class="tabcontent active">
        <h3>Login</h3>
        <form id="userLoginForm" onsubmit="userLogin(event)">
          <label>Email ID <input type="email" required /></label>
          <label>Password <input type="password" required /></label>
          <button type="submit">Login</button>
        </form>
        <span class="link" onclick="showUserRegister()">Register here</span>
      </div>
      <!-- EMPLOYEE TAB -->
      <div class="tabcontent">
        <h3>Employee Login</h3>
        <form id="empLoginForm" onsubmit="empLogin(event)">
          <label>Email ID <input type="email" required /></label>
          <label>Password <input type="password" required /></label>
          <button type="submit">Login</button>
        </form>
        <span class="link" onclick="showEmployeeRegister()">Register here</span>
      </div>
      <!-- ADMIN TAB -->
      <div class="tabcontent">
        <h3>Admin Login</h3>
        <form id="adminLoginForm" onsubmit="adminLogin(event)">
          <label>Username <input type="text" required /></label>
          <label>Password <input type="password" required /></label>
          <button type="submit">Login</button>
        </form>
        <div style="color:#c0392b">
          <b>Demo login: admin / admin123</b>
        </div>
      </div>
    </section>

    <!-- User Register Page -->
    <section id="userRegister" class="hide">
      <h2>User Registration</h2>
      <form onsubmit="registerUser(event)">
        <label>First Name <input type="text" required /></label>
        <label>Last Name <input type="text" required /></label>
        <label>Email ID <input type="email" required /></label>
        <label>Contact Number <input type="tel" required /></label>
        <label>Password <input type="password" required /></label>
        <label>Gender
          <select required>
            <option value="">Select</option>
            <option>Male</option>
            <option>Female</option>
          </select>
        </label>
        <button type="submit">Register</button>
      </form>
      <span class="link" onclick="backToHome()">Back to Login</span>
    </section>

    <!-- Employee Register Page -->
    <section id="employeeRegister" class="hide">
      <h2>Employee Registration</h2>
      <form onsubmit="registerEmployee(event)">
        <label>Full Name <input type="text" required /></label>
        <label>Email ID <input type="email" required /></label>
        <label>Password <input type="password" required /></label>
        <label>Salary <input type="number" min="0" placeholder="Optional" /></label>
        <button type="submit">Register</button>
      </form>
      <span class="link" onclick="backToEmpLogin()">Back to Employee Login</span>
    </section>

    <!-- User Step 1: Plants -->
    <section id="plantsPage" class="hide">
      <h2>Plant Details</h2>
      <table>
        <tr>
          <th>Image</th>
          <th>Plant ID</th>
          <th>Plant Name</th>
          <th>Soil Type</th>
        </tr>
        <tr>
          <td><img src="https://images.unsplash.com/photo-1506744038136-46273834b3fb?fit=crop&w=200&q=80" alt="Tomato" class="plant-img" /></td>
          <td>1001</td>
          <td>Tomato</td>
          <td>Loamy</td>
        </tr>
        <tr>
          <td><img src="https://images.unsplash.com/photo-1464983953574-0892a716854b?fit=crop&w=200&q=80" alt="Rice" class="plant-img" /></td>
          <td>1002</td>
          <td>Rice</td>
          <td>Clay</td>
        </tr>
        <tr>
          <td><img src="https://images.unsplash.com/photo-1464226184884-fa280b87c399?fit=crop&w=200&q=80" alt="Spinach" class="plant-img" /></td>
          <td>1003</td>
          <td>Spinach</td>
          <td>Sandy</td>
        </tr>
        <tr>
          <td><img src="https://images.unsplash.com/photo-1465101046530-73398c7f28ca?fit=crop&w=200&q=80" alt="Potato" class="plant-img" /></td>
          <td>1004</td>
          <td>Potato</td>
          <td>Sandy Loam</td>
        </tr>
      </table>
      <div class="nav-btns">
        <button onclick="userLogout()">Back</button>
        <button onclick="showMedicines()">Next</button>
      </div>
    </section>

    <!-- User Step 2: Medicines -->
    <section id="medicinesPage" class="hide">
      <h2>Medicine Details</h2>
      <table>
        <tr>
          <th>Image</th>
          <th>Medicine ID</th>
          <th>Name</th>
          <th>Type</th>
          <th>Cost</th>
        </tr>
        <tr>
          <td><img src="https://images.unsplash.com/photo-1518998053901-5348d3961a73?fit=crop&w=200&q=80" alt="Pesticide A" class="plant-img" /></td>
          <td>M101</td>
          <td>Pesticide A</td>
          <td>Pesticide</td>
          <td>₹200</td>
        </tr>
        <tr>
          <td><img src="https://images.unsplash.com/photo-1444392061819-9df71a51d1c9?fit=crop&w=200&q=80" alt="Fungicide B" class="plant-img" /></td>
          <td>M102</td>
          <td>Fungicide B</td>
          <td>Fungicide</td>
          <td>₹150</td>
        </tr>
        <tr>
          <td><img src="https://images.unsplash.com/photo-1465101162946-4377e57745c3?fit=crop&w=200&q=80" alt="Herbicide C" class="plant-img" /></td>
          <td>M103</td>
          <td>Herbicide C</td>
          <td>Herbicide</td>
          <td>₹180</td>
        </tr>
      </table>
      <div class="nav-btns">
        <button onclick="showPlants()">Back</button>
        <button onclick="showMethods()">Next</button>
      </div>
    </section>

    <!-- User Step 3: Methods -->
    <section id="methodsPage" class="hide">
      <h2>Method Details</h2>
      <table>
        <tr>
          <th>Method ID</th>
          <th>Name</th>
          <th>Type</th>
        </tr>
        <tr>
          <td>MT01</td>
          <td>Drip Irrigation</td>
          <td>Irrigation</td>
        </tr>
        <tr>
          <td>MT02</td>
          <td>Organic Farming</td>
          <td>Farming</td>
        </tr>
        <tr>
          <td>MT03</td>
          <td>Mulching</td>
          <td>Soil Management</td>
        </tr>
      </table>
      <div class="nav-btns">
        <button onclick="showMedicines()">Back</button>
        <button onclick="userLogout()">Logout</button>
      </div>
    </section>

    <!-- Employee Dashboard -->
    <section id="employeeDashboard" class="hide">
      <h2>Employee Dashboard</h2>
      <div class="dashboard-module">
        <h3>Add Plant</h3>
        <form>
          <label>Plant ID <input type="text" placeholder="Plant ID" /></label>
          <label>Name <input type="text" placeholder="Plant Name" /></label>
          <label>Soil Type <input type="text" placeholder="Soil Type" /></label>
          <button type="button" onclick="alert('Demo: Plant Added!')">Add Plant</button>
        </form>
      </div>
      <div class="dashboard-module">
        <h3>Add Medicine</h3>
        <form>
          <label>Medicine ID <input type="text" placeholder="Medicine ID" /></label>
          <label>Name <input type="text" placeholder="Medicine Name" /></label>
          <label>Type <input type="text" placeholder="Type" /></label>
          <label>Cost <input type="text" placeholder="Cost" /></label>
          <button type="button" onclick="alert('Demo: Medicine Added!')">Add Medicine</button>
        </form>
      </div>
      <div class="dashboard-module">
        <h3>Add Method</h3>
        <form>
          <label>Method ID <input type="text" placeholder="Method ID" /></label>
          <label>Name <input type="text" placeholder="Method Name" /></label>
          <label>Type <input type="text" placeholder="Type" /></label>
          <button type="button" onclick="alert('Demo: Method Added!')">Add Method</button>
        </form>
      </div>
      <button onclick="empLogout()">Logout</button>
    </section>

    <!-- Admin Dashboard -->
    <section id="adminDashboard" class="hide">
      <h2>Admin Dashboard</h2>
      <div class="dashboard-module">
        <h3>1. User List</h3>
        <input type="text" placeholder="Search by Contact Number" style="margin-bottom: 1rem" />
        <table>
          <tr>
            <th>First Name</th>
            <th>Last Name</th>
            <th>Email</th>
            <th>Contact</th>
            <th>Password</th>
          </tr>
          <tr>
            <td>Ravi</td>
            <td>Kumar</td>
            <td>ravi@gmail.com</td>
            <td>9123456789</td>
            <td>******</td>
          </tr>
        </table>
      </div>
      <div class="dashboard-module">
        <h3>2. Employee List</h3>
        <input type="text" placeholder="Search by Email" style="margin-bottom: 1rem" />
        <table>
          <tr>
            <th>Name</th>
            <th>Email</th>
            <th>Password</th>
            <th>Salary</th>
            <th>Action</th>
          </tr>
          <tr>
            <td>Arjun</td>
            <td>arjun@farm.com</td>
            <td>******</td>
            <td>₹18,000</td>
            <td>
              <button class="btn-table" onclick="alert('Demo: Employee Removed')">Delete</button>
            </td>
          </tr>
        </table>
      </div>
      <div class="dashboard-module">
        <h3>3. Plant List</h3>
        <table>
          <tr>
            <th>ID</th>
            <th>Name</th>
            <th>Soil Type</th>
          </tr>
          <tr>
            <td>1001</td>
            <td>Tomato</td>
            <td>Loamy</td>
          </tr>
        </table>
      </div>
      <div class="dashboard-module">
        <h3>4. Medicine List</h3>
        <table>
          <tr>
            <th>ID</th>
            <th>Name</th>
            <th>Type</th>
            <th>Cost</th>
          </tr>
          <tr>
            <td>M101</td>
            <td>Pesticide A</td>
            <td>Pesticide</td>
            <td>₹200</td>
          </tr>
        </table>
      </div>
      <div class="dashboard-module">
        <h3>5. Method List</h3>
        <table>
          <tr>
            <th>ID</th>
            <th>Name</th>
            <th>Type</th>
          </tr>
          <tr>
            <td>MT01</td>
            <td>Drip Irrigation</td>
            <td>Irrigation</td>
          </tr>
        </table>
      </div>
      <div class="dashboard-module">
        <h3>6. Add Employee</h3>
        <form>
          <label>Name <input type="text" placeholder="Employee Name" /></label>
          <label>Email <input type="email" placeholder="Employee Email" /></label>
          <label>Password <input type="password" placeholder="Password" /></label>
          <label>Salary <input type="text" placeholder="Salary" /></label>
          <button type="button" onclick="alert('Demo: Employee Added!')">Add Employee</button>
        </form>
      </div>
      <div class="dashboard-module">
        <h3>7. View User Feedback/Queries</h3>
        <table>
          <tr>
            <th>Name</th>
            <th>Email</th>
            <th>Contact</th>
            <th>Message</th>
          </tr>
          <tr>
            <td>Ajay</td>
            <td>ajay@xyz.com</td>
            <td>9876543210</td>
            <td>How to register as employee?</td>
          </tr>
        </table>
      </div>
      <button onclick="adminLogout()">Logout</button>
    </section>

    <!-- About Us -->
    <section id="aboutSection" class="hide">
      <h2>About Us</h2>
      <div class="section">
        <p>
          Our Farm Management System brings modern IT solutions to agriculture. We connect
          farmers, employees, and administrators to improve efficiency and transparency in
          farm management.
          <br />
          <b>Key Features:</b>
          <ul>
            <li>Easy-to-use dashboard for users, employees, and admin.</li>
            <li>Plant, medicine, and method database for improved farm operations.</li>
            <li>Secure access and staff management tools.</li>
          </ul>
        </p>
      </div>
    </section>

    <!-- Contact Page -->
    <section id="contactSection" class="hide">
      <h2>Contact Us</h2>
      <form onsubmit="submitContactForm(event)">
        <label>Name <input type="text" placeholder="Your Name" required /></label>
        <label>Email <input type="email" placeholder="Your Email" required /></label>
        <label>Contact Number <input type="tel" placeholder="Phone Number" required /></label>
        <label>
          Your Message
          <textarea rows="4" placeholder="Feedback or Query" required></textarea>
        </label>
        <button type="submit">Submit</button>
      </form>
    </section>

  </div>

  <script>
    // Page Navigation
    function showPage(pg) {
      document.getElementById('homeSection').style.display = pg === 'home' ? '' : 'none';
      document.getElementById('aboutSection').style.display = pg === 'about' ? '' : 'none';
      document.getElementById('contactSection').style.display = pg === 'contact' ? '' : 'none';
      document.getElementById('userRegister').classList.add('hide');
      document.getElementById('employeeRegister').classList.add('hide');
      hideDashboards();
      ['plantsPage', 'medicinesPage', 'methodsPage'].forEach(id => {
        let el = document.getElementById(id);
        if (el) el.classList.add('hide');
      });
      // Reset all tabs to User tab on home page for consistency
      if(pg === 'home') showTab(0);
    }

    // Tabs for Home page (User, Employee, Admin)
    function showTab(tabIndex) {
      let tabs = document.getElementsByClassName('tab');
      let tabconts = document.getElementsByClassName('tabcontent');
      for (let i = 0; i < tabs.length; i++) {
        tabs[i].classList.remove('active');
        tabconts[i].classList.remove('active');
      }
      tabs[tabIndex].classList.add('active');
      tabconts[tabIndex].classList.add('active');
    }

    // ----- USER -----
    function showUserRegister() {
      document.getElementById('homeSection').style.display = 'none';
      document.getElementById('userRegister').classList.remove('hide');
    }
    function backToHome() {
      document.getElementById('userRegister').classList.add('hide');
      document.getElementById('homeSection').style.display = '';
      showTab(0);
    }
    function registerUser(e) {
      e.preventDefault();
      alert('Registration successful! Now Login.');
      backToHome();
    }
    function userLogin(e) {
      e.preventDefault();
      document.getElementById('homeSection').style.display = 'none';
      showPlants();
    }
    function userLogout() {
      hideAllSections();
      document.getElementById('homeSection').style.display = '';
      showTab(0);
    }
    function showPlants() {
      hideAllSections();
      document.getElementById('plantsPage').classList.remove('hide');
    }
    function showMedicines() {
      hideAllSections();
      document.getElementById('medicinesPage').classList.remove('hide');
    }
    function showMethods() {
      hideAllSections();
      document.getElementById('methodsPage').classList.remove('hide');
    }

    // ----- EMPLOYEE -----
    function showEmployeeRegister() {
      document.getElementById('homeSection').style.display = 'none';
      document.getElementById('employeeRegister').classList.remove('hide');
    }
    function backToEmpLogin() {
      document.getElementById('employeeRegister').classList.add('hide');
      document.getElementById('homeSection').style.display = '';
      showTab(1);
    }
    function registerEmployee(e) {
      e.preventDefault();
      alert('Employee registration successful! Now Login as Employee.');
      backToEmpLogin();
    }
    function empLogin(e) {
      e.preventDefault();
      document.getElementById('homeSection').style.display = 'none';
      document.getElementById('employeeDashboard').classList.remove('hide');
    }
    function empLogout() {
      hideDashboards();
      document.getElementById('homeSection').style.display = '';
      showTab(1);
    }

    // ----- ADMIN -----
    function adminLogin(e) {
      e.preventDefault();
      let user = document.querySelector('#adminLoginForm input[type="text"]').value.trim();
      let pass = document.querySelector('#adminLoginForm input[type="password"]').value.trim();
      if (user === 'admin' && pass === 'admin123') {
        document.getElementById('homeSection').style.display = 'none';
        document.getElementById('adminDashboard').classList.remove('hide');
      } else {
        alert('Invalid admin credentials!');
      }
    }
    function adminLogout() {
      hideDashboards();
      document.getElementById('homeSection').style.display = '';
      showTab(2);
    }

    // Helpers
    function hideDashboards() {
      document.getElementById('employeeDashboard').classList.add('hide');
      document.getElementById('adminDashboard').classList.add('hide');
    }
    function hideAllSections() {
      document.getElementById('homeSection').style.display = 'none';
      document.getElementById('userRegister').classList.add('hide');
      document.getElementById('employeeRegister').classList.add('hide');
      document.getElementById('employeeDashboard').classList.add('hide');
      document.getElementById('adminDashboard').classList.add('hide');
      document.getElementById('aboutSection').style.display = 'none';
      document.getElementById('contactSection').style.display = 'none';
      ['plantsPage', 'medicinesPage', 'methodsPage'].forEach(id => {
        let el = document.getElementById(id);
        if(el) el.classList.add('hide');
      });
    }

    // Contact form submission
    function submitContactForm(e) {
      e.preventDefault();
      alert('Demo: Message sent!');
      document.querySelector('#contactSection form').reset();
    }

    // On page load initialize to Home and User tab active
    showPage('home');
  </script>
</body>
</html>
