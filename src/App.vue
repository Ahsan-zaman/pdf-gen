<template>
<div>
	<input type="text" name="" v-model="name" id="">
	<input type="text" name="" v-model="CourseName" id="">
	<input type="text" name="" v-model="date" id="">
	<div class="button" @click="gen">generate pdf</div>
	<div id="app">
		<div style="width:842px; height:595px; padding:20px; text-align:center;margin:auto; border: 10px solid #787878">
		<div style="width:792px; height:545px; padding:20px; text-align:center; border: 5px solid #787878">
				<br><br><br><br>
				<span style="font-size:50px; font-weight:bold">Certificate of Completion</span>
				<br><br>
				<span style="font-size:25px"><i>This is to certify that</i></span>
				<br><br>
				<span style="font-size:30px"><b>{{name}}</b></span><br/><br/>
				<span style="font-size:25px"><i>has completed the course</i></span> <br/><br/>
				<span style="font-size:30px">{{CourseName}}</span> <br/><br/>
				<span style="font-size:20px">with score of <b>99%</b></span> <br/><br/><br/>
				<span style="font-size:25px"><i>dated</i></span><br>
				{{date}}<br>
				<!-- <span style="font-size:30px">$dt</span> -->
		</div>
		</div>
	</div>
	
</div>
</template>

<script>
// import jsPDF from 'jspdf'
import axios from 'axios'
// import HelloWorld from './components/HelloWorld.vue'

export default {
	name: 'app',
	// components: {
	// 	HelloWorld
	// },
	data(){
		return{
			name:'محمد احسان الزمان',
			CourseName: 'Course Name',
			date: new Date().toISOString().substr(0,10),
		}
	},
	methods:{
		gen(){
			var divContents = document.getElementById('app').innerHTML;
			// var printWindow = window.open('', '', 'height=400,width=800');
			// printWindow.document.write('<html><head><title>DIV Contents</title>');
			// printWindow.document.write('</head><body >');
			// printWindow.document.write(divContents);
			// printWindow.document.write('</body></html>');
			// printWindow.document.close();
			// printWindow.print();


			// let pdfName = 'test'; 
			// var doc = new jsPDF();
			// doc.text(divContents, 10, 10);
			// doc.save(pdfName + '.pdf');
			// var printDoc = new jsPDF();
			// printDoc.fromHTML(document.getElementById('app').innerHTML, 15, 15, {
			// 	'width': 170,
			// });
			// printDoc.save('sample-file.pdf');
			// printDoc.fromHTML(divContents, 10, 10, {'width': 180});
			// printDoc.autoPrint();
			// printDoc.output("dataurlnewwindow");
			var endpoint = "https://v2018.api2pdf.com/chrome/html"
			var apiKey = "4d6c0a01-bf2d-45a6-afab-70a315cf26a7"
			var config = {
				headers: {
				Authorization: apiKey
				}
			}
			var content = '<html><head><meta charset="UTF-8"></head><body style="background: #f1f1f1;background-size: cover;">' + divContents + '</body></html>'
			var payload = {
				html: content, //Use your own HTML
				inlinePdf: true,
				options: {
					landscape : true
				}
			}
			axios.post(endpoint, payload, config)
			.then(function(response) {
				window.open(response.data.pdf)
				// alert(response.data.pdf); //this is your PDF! Do something with it
			})
			.catch(function(error) {
				alert(error);
			});
		},
		// gendl(){
		// 	var divContents = document.getElementById('app').innerHTML;
		// 	var endpoint = "https://v2018.api2pdf.com/chrome/html"
		// 	var apiKey = "4d6c0a01-bf2d-45a6-afab-70a315cf26a7"
		// 	var config = {
		// 		headers: {
		// 		Authorization: apiKey
		// 		}
		// 	}
		// 	var content = '<html><head><meta charset="UTF-8"></head><body>' + divContents + '</body></html>'
		// 	var payload = {
		// 		html: content, //Use your own HTML
		// 		inlinePdf: true,
		// 		options: {
		// 			landscape : true
		// 		}
		// 	}
		// 	axios.post(endpoint, payload, config)
		// 	.then(function(response) {
		// 		var link = document.createElement("a");
		// 		link.href = response.data.pdf;
		// 		link.setAttribute("download");
		// 		link.click();
		// 		document.body.removeChild(link);
		// 		// delete link;
		// 	})
		// 	.catch(function(error) {
		// 		alert(error);
		// 	});
		// }
	}
}
</script>

<style>
#app {
	font-family: 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}
input{
	font-size: 1.2rem;
	padding: 10px
}
.button{
	display: inline;
	text-transform: uppercase;
	padding: 10px 20px;
	margin-left: 50px;
	background-color: #2c3e50;
	color: #fff;
	cursor: pointer;
}
</style>
