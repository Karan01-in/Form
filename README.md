<!DOCTYPE html>
<html>
<head>
    <title>Form</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        .form-container {
            max-width: 600px;
            margin: auto;
            border: 1px solid #ccc;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        .form-container h2 {
            text-align: center;
        }
        .form-group {
            margin-bottom: 15px;
        }
        .form-group label {
            display: block;
            margin-bottom: 5px;
        }
        .form-group input, .form-group select, .form-group textarea {
            width: 100%;
            padding: 8px;
            box-sizing: border-box;
        }
        #generate-pdf {
            display: block;
            margin: 20px auto;
            padding: 10px 20px;
            background-color: #ebf3eb;
            color: rgb(0, 0, 0);
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
    </style>
</head>
<body>

<div class="form-container">
    <h2>Division District Hospital Azamgardh U.P</h2>
    <form id="form">
        <div class="form-group">
            <label for="title" style="text-align: center; display: block;">Form No.</label>
            <input type="number" id="title" name="title" required style="text-align: center;">
        </div>
        <div class="form-group">
            <label for="datetime">Date and Time:</label>
            <input type="datetime-local" id="datetime" name="datetime" required>
        </div>
        <div class="form-group">
            <label for="fir_no">FIR No/Section:</label>
            <input type="text" id="fir_no" name="fir_no" required>
        </div>
        <div class="form-group">
            <label for="mlc_no">MLC No:</label>
            <input type="text" id="mlc_no" name="mlc_no" required>
        </div>
        <div class="form-group">
            <label for="mark_identification">Mark Identification:</label>
            <input type="text" id="mark_identification" name="mark_identification" required>
        </div>
        <div class="form-group">
            <label for="name">Name:</label>
            <input type="text" id="name" name="name" required>
        </div>
        <div class="form-group">
            <label for="age_sex">Age/Sex:</label>
            <input type="text" id="age_sex" name="age_sex" required>
        </div>
        <div class="form-group">
            <label for="relation">Son/Daughter/Wife/Husband:</label>
            <input type="text" id="relation" name="relation" required>
        </div>
        <div class="form-group">
            <label for="village">Village/Address:</label>
            <textarea id="village" name="village" rows="4" required></textarea>
        </div>
        <div class="form-group">
            <label for="police_station">Police Station:</label>
            <input type="text" id="police_station" name="police_station" required>
        </div>
        <div class="form-group">
            <label for="district">District:</label>
            <input type="text" id="district" name="district" required>
        </div>
        <div class="form-group">
            <label for="state">State:</label>
            <input type="text" id="state" name="state" required>
        </div>
        <div class="form-group">
            <label for="mobile_no">Mobile No:</label>
            <input type="tel" id="mobile_no" name="mobile_no" required>
        </div>
        <div class="form-group">
            <label for="details_of_injuries">Details of Injuries:</label>
            <textarea id="details_of_injuries" name="details_of_injuries" rows="4" required></textarea>
        </div>
        <div class="form-group">
            <label for="opinion">Opinion:</label>
            <textarea id="opinion" name="opinion" rows="4" required></textarea>
        </div>
    </form>
    <button id="generate-pdf">Generate PDF</button>
</div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.3.1/jspdf.umd.min.js"></script>
<script>
    document.getElementById('generate-pdf').addEventListener('click', function () {
        const { jsPDF } = window.jspdf;
        const doc = new jsPDF();

        doc.text("Form", 20, 20);

        const formElements = document.getElementById('form').elements;

        let y = 40;
        for (let i = 0; i < formElements.length; i++) {
            const element = formElements[i];
            if (element.type !== 'submit' && element.type !== 'button') {
                doc.text(`${element.previousElementSibling.textContent} ${element.value}`, 20, y);
                y += 10;
            }
        }

        doc.save('form.pdf');
    });
</script>

</body>
</html>
