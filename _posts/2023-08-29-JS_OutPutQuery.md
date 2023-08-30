---
layout: post
title: Data Table of Boba 
description: A JS Styled Table displaying boba and its diffrent types.
type: hacks
courses: {'csse': {'week': 2}, 'csp': {'week': 2}, 'csa': {'week': 0}}
categories: ['C4.1']
---




<html>
<head>
    <style>
        /* Add inline CSS for styling */
        body {
            font-family: Arial, sans-serif;
        }
        table {
            width: 80%;
            margin: 20px auto;
            border-collapse: collapse;
            border: 1px solid #ccc;
        }
        th, td {
            padding: 10px;
            text-align: left;
            border-bottom: 1px solid #ccc;
        }
        th {
            background-color: #f2f2f2;
        }
        /* Improved styling with gradient background and text color */
        tbody tr:nth-child(odd) {
            background: linear-gradient(to right, #ffe6e6, #ffb3b3);
        }
        tbody tr:nth-child(even) {
            background: linear-gradient(to right, #e6faff, #b3e0ff);
        }
        td {
            font-weight: bold;
            color: white; /* Set text color to match gradient */
        }
    </style>
    <script type="text/javascript" language="javascript" src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script type="text/javascript" language="javascript" src="https://cdn.datatables.net/1.13.4/js/jquery.dataTables.min.js"></script>
</head>
<body>
    <table id="bobaTable">
        <thead>
            <tr>
                <th>Boba Tea Type</th>
                <th>Description</th>
                <th>Cost</th>
            </tr>
        </thead>
        <tbody style="">
            <tr>
                <td style="font-weight: bold; color: black;">Brown Sugar Milk Tea</td>
                <td style="color: black;">Black Tea mixed with brown sugar and honey boba</td>
                <td style="color: black;">$5.50</td>
            </tr>
            <tr>
                <td style="font-weight: bold; color: black;">Taro Milk Tea</td>
                <td style="color: black;">Rich and creamy taro flavor</td>
                <td style="color: black;">$5.50</td>
            </tr>
            <tr>
                <td style="font-weight: bold; color: black;">Thai Milk Tea</td>
                <td style="color: black;">Strong black tea with condensed milk</td>
                <td style="color: black;">$6.00</td>
            </tr>
            <tr>
                <td style="font-weight: bold; color: black;">Matcha Latte</td>
                <td style="color: black;">Green tea flavor with a hint of sweetness</td>
                <td style="color: black;">$6.00</td>
            </tr>
            <tr>
                <td style="font-weight: bold; color: black;">Honeydew Milk Tea</td>
                <td style="color: black;">Refreshing honeydew flavor</td>
                <td style="color: black;">$4.75</td>
            </tr>
            <tr>
                <td style="font-weight: bold; color: black;">Strawberry Jasmine Tea</td>
                <td style="color: black;">Light and floral jasmine tea with strawberry</td>
                <td style="color: black;">$6.25</td>
            </tr>
            <tr>
                <td style="font-weight: bold; color: black;">Mango Green Tea</td>
                <td style="color: black;">Fruity mango combined with green tea</td>
                <td style="color: black;">$6.50</td>
            </tr>
            <tr>
                <td style="font-weight: bold; color: black;">Classic Bubble Tea</td>
                <td style="color: black;">Traditional black tea with chewy tapioca pearls</td>
                <td style="color: black;">$5.25</td>
            </tr>
            <tr>
                <td style="font-weight: bold; color: black;">Jasmine Milk Tea</td>
                <td style="color: black;">Delicate jasmine tea combined with milk</td>
                <td style="color: black;">$5.75</td>
            </tr>
            <tr>
                <td style="font-weight: bold; color: black;">Coconut Cream Tea</td>
                <td style="color: black;">Coconut-infused tea with a creamy texture</td>
                <td style="color: black;">$5.50</td>
            </tr>
        </tbody>
    </table>
    <script>
        $("#bobaTable").DataTable();
    </script>
</body>
</html>

