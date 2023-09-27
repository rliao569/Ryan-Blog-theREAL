---
toc: False
comments: False
layout: post
title: data table
description: data table for popular computers
courses: {'csp': {'week': 3}}
categories: ['C3.4']
type: tangibles
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- Load jQuery and DataTables output style and scripts -->
    <link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.13.4/css/jquery.dataTables.min.css">
    <script type="text/javascript" language="javascript" src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script>var define = null;</script>
    <script type="text/javascript" language="javascript" src="https://cdn.datatables.net/1.13.4/js/jquery.dataTables.min.js"></script>
</head>
<body>
    <table id="demo" class="table">
        <thead>
            <tr>
                <th>Name</th>
                <th>Company</th>
                <th>Year</th>
                <th>CPU</th>
                <th>Price</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Lenovo ThinkPad X1 Carbon Gen 10</td>
                <td>Lenovo</td>
                <td>2022</td>
                <td>Intel Core i7-1260P</td>
                <td>$1,299</td>
            </tr>
            <tr>
                <td>HP Spectre x360 16</td>
                <td>HP</td>
                <td>2022</td>
                <td>Intel Core i7-12700H</td>
                <td>$1,399</td>
            </tr>
            <tr>
                <td>Dell XPS 13 Plus</td>
                <td>Dell</td>
                <td>2022</td>
                <td>Intel Core i7-1250U</td>
                <td>$1,299</td>
            </tr>
            <tr>
                <td>Apple MacBook Pro 14</td>
                <td>Apple</td>
                <td>2021</td>
                <td>M1 Pro</td>
                <td>$1,999</td>
            </tr>
            <tr>
                <td>Microsoft Surface Laptop Studio</td>
                <td>Microsoft</td>
                <td>2021</td>
                <td>Intel Core i7-11370H</td>
                <td>$1,599</td>
            </tr>
            <tr>
                <td>Lenovo ThinkPad X1 Nano Gen 2</td>
                <td>Lenovo</td>
                <td>2022</td>
                <td>Intel Core i7-1280P</td>
                <td>$1,499</td>
            </tr>
            <tr>
                <td>Asus ZenBook Flip S 13 OLED</td>
                <td>Asus</td>
                <td>2022</td>
                <td>Intel Core i7-1260P</td>
                <td>$1,299</td>
            </tr>
            <tr>
                <td>Acer Swift X</td>
                <td>Acer</td>
                <td>2022</td>
                <td>AMD Ryzen 7 5800U</td>
                <td>$999</td>
            </tr>
            <tr>
                <td>Dell XPS 15</td>
                <td>Dell</td>
                <td>2022</td>
                <td>Intel Core i7-12700H</td>
                <td>$1,499</td>
            </tr>
            <tr>
                <td>HP Envy 14</td>
                <td>HP</td>
                <td>2022</td>
                <td>AMD Ryzen 7 5800U</td>
                <td>$999</td>
            </tr>
            <tr>
                <td>Apple Mac Mini M2 (2023)</td>
                <td>Apple</td>
                <td>2023</td>
                <td>Apple M2 chip</td>
                <td>$599</td>
            </tr>
        </tbody>
    </table>
    <!-- Script is used to embed executable code -->
    <script>
        $("#demo").DataTable();
    </script>
</body>
</html>

