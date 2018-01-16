<template>
  <div class="row" id="app">

<!-- Nav Bar -->      
<nav class="navbar navbar-default">
  <div class="container-fluid"> 
    <div class="navbar-header">
      <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1">
        <span class="sr-only">Toggle navigation</span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
      </button>
      <a class="navbar-brand" href="#">Currency Converter</a>
    </div>

   
    <div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
      <ul class="nav navbar-nav">
        <li class="active"><a href="#">Link <span class="sr-only">(current)</span></a></li>
        <li><a href="#">Link</a></li>
      </ul>
    </div>
  </div>
</nav>

<!-- Nav Bar -->

<div class="container">
    <div class="col-md-12">
    <div class="panel panel-default">
        <div id="header-color" class="panel-heading">
            <h3 id="title-text" class="title-panel">Currency Converter</h3> 
            <span class="flag-icon flag-icon-us"></span>
            <span class="flag-icon flag-icon-ro"></span>
            <span class="flag-icon flag-icon-es"></span>
            <span class="flag-icon flag-icon-de"></span>
        </div>
    	<currency></currency>
    </div>
    </div>
    <div class="col-md-12">
    <div class="panel panel-default">
        <div class="panel-heading">
            <h3 class="title-panel">Your latest conversions</h3> 
        </div>
    <div class="col-xs-12 col-sm-12 col-md-12">    
    <div class="button-convert">
    <button v-bind="newCurr" id="store-rate" type="button" class="btn btn-success" @click="addCurr">Store Conversions</button>
    </div>
    <div class="button-convert">
    <button id="store-rate" type="button" class="btn btn-danger" @click="clearList">Clear List</button>
    </div>
    </div>
        <div class="col-xs-12 col-sm-12 col-md-12">
        <div id="alert-box" class="alert alert-warning">
          <a href="#" class="close" data-dismiss="alert" aria-label="close">&times;</a>
          <strong>Notice!</strong> You can save up to 100 conversions, wich will be stored for 30 days.
        </div>
        </div>
<table id="tablestore" class="table table-bordered">
  <thead>
    <tr>
      <th scope="col">#</th>
      <th scope="col">Date</th>
      <th scope="col">Conversions</th>
    </tr>
  </thead>
  <tbody v-bind="curr in currs">
    <tr>
      <th scope="row">1</th>
      <td></td>
      <td>{{ curr.text }}</td>
      <!--<button class="delete" @click="removeCurr(curr)">X</button>-->
    </tr>
    <tr>
      <th scope="row">2</th>
      <td></td>
      <td>{{ curr.text }}</td>
      <!--<button class="delete" @click="removeCurr(curr)">X</button>-->
    </tr>
    <tr>
      <th scope="row">3</th>
      <td></td>
      <td>{{ curr.text }}</td>
      <!--<button class="delete" @click="removeCurr(curr)">X</button>-->
    </tr>
  </tbody>
</table>
      <h5 class="u-text-center"></h5>
    </div>
    </div>  
  </div>
  </div>
</template>

<script>
import Currency from './components/Currency'

export default {
  name: 'app',
  components: {
    Currency
  },
  data () {
    return {
      newCurr: "",
      currs: [
			],
      curr : ""
    }
  },
  computed: {
			areAllSelected: function () {
				return this.currs.every(function(curr) {
					return curr.checked;
				}) &&  this.currs.length > 0;
			},
		},
  methods: {
    addCurr: function () {
				var curr = this.newCurr.trim();
        console.log( Currency );
				if (curr) {
					this.currs.push({text: curr});
					this.newCurr = "";
          console.log(this.currs);
				}
		},
    removeCurr: function (curr) {
        var index = this.currs.indexOf(curr);
				this.currs.splice(index, 1);
		},
    clearList: function () {
				this.currs = [

				];
		},
    // showText: function(val) {      
    //   console.log(val);
    // }
  }

}

</script>

<style>

</style>
