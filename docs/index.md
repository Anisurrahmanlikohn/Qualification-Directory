
<html>
<head>
<title>Add more Qualification</title>
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css" />
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/js/bootstrap.min.js"></script>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/2.2.0/jquery.min.js"></script>
</head>
<body>
<div class="container">
<br />
<br />
<h2 align="center">Add or Remove Your Qualification</a></h2><br />
<div class="form-group">
<form name="add_name" id="add_name">
<div class="table-responsive">
<h4>Enter Your Name:</h4>

<table  class="table table-bordered" >
<tr>
<td><input type="text" name="person" placeholder="Enter Your Name" class="form-control name_list"  /></td>
</tr>

</table><br>
<h4> Enter Your Qualification:</h4>
<table  class="table table-bordered" id="dynamic_field">
<tr>
<th>Exam Name</th>
<th>Action</th>
</tr>
<tr>
<td><input type="text" name="name[]"  class="form-control name_list" /></td>
<td><button type="button" name="add" id="add" class="btn btn-success">Add More</button></td>
</tr>
</table>
<input type="button" name="submit" id="submit" class="btn btn-info" value="Submit" />
</div> <br>
</form>
</div>

</div>
<div>
</div>
</body>
</html>

<script>
$(document).ready(function(){
var i=1;
$('#add').click(function(){
i++;
$('#dynamic_field').append('<tr id="row'+i+'"><td><input type="text" name="name[]"  class="form-control name_list" /></td><td><button type="button" name="remove" id="'+i+'" class="btn btn-danger btn_remove">X</button></td></tr>');
});

$(document).on('click', '.btn_remove', function(){
var button_id = $(this).attr("id"); 
$('#row'+button_id+'').remove();
});

$('#submit').click(function(){		
$.ajax({
url:"db.php",
method:"POST",
data:$('#add_name').serialize(),
success:function(data)
{
alert(data);
$('#add_name')[0].reset();
}
});
});

});
</script>




