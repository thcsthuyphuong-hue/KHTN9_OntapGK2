<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<title>Quản lý kết quả học sinh</title>

<script src="https://cdn.tailwindcss.com"></script>

</head>

<body class="bg-gray-100 p-6">

<h1 class="text-2xl font-bold text-blue-700 mb-6">
Bảng kết quả học sinh
</h1>

<div class="bg-white p-4 rounded shadow">

<table class="w-full border">

<thead class="bg-blue-100">
<tr>
<th class="border p-2">Họ tên</th>
<th class="border p-2">SBD</th>
<th class="border p-2">Lớp</th>
<th class="border p-2">Trường</th>
<th class="border p-2">Điểm</th>
</tr>
</thead>

<tbody id="result-table"></tbody>

</table>

</div>

<script type="module">

import { initializeApp } from "https://www.gstatic.com/firebasejs/10.7.0/firebase-app.js";
import { getFirestore, collection, getDocs } from "https://www.gstatic.com/firebasejs/10.7.0/firebase-firestore.js";

const firebaseConfig = {
 apiKey: "AIzaSyC5zISc-3_Fc-NZRrqrA4OezGGNR3j6kMQ",
 authDomain: "khtn9-ontapgk2.firebaseapp.com",
 projectId: "khtn9-ontapgk2",
 storageBucket: "khtn9-ontapgk2.appspot.com",
 messagingSenderId: "1054675478842",
 appId: "1:1054675478842:web:54e8bb2dbf3e5aec6c0803"
};

const app = initializeApp(firebaseConfig);
const db = getFirestore(app);

async function loadData(){

const querySnapshot = await getDocs(collection(db,"results"));

let html="";

querySnapshot.forEach((doc)=>{

const d=doc.data();

html+=`
<tr>
<td class="border p-2">${d.name}</td>
<td class="border p-2">${d.sbd}</td>
<td class="border p-2">${d.class}</td>
<td class="border p-2">${d.school}</td>
<td class="border p-2 font-bold text-blue-600">${d.score}</td>
</tr>
`;

});

document.getElementById("result-table").innerHTML=html;

}

loadData();

</script>

</body>
</html>
