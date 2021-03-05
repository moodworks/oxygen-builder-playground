# oxygen-builder-playground

fullpage.js code to add to code block > js


jQuery(document).ready(function($) {

    if(jQuery('html').attr('ng-app') == 'CTFrontendBuilder') return;
    jQuery(".pozadina").css("background-color", "#eae8d4");
  	jQuery(".krug").css("transform", "rotate(0deg)"); 
  	jQuery("#section-175-30").css("display", "none"); //gumbi na kraju kontakt i o nama
    jQuery(".section").css("background-color", "transparent");
    jQuery(".pozadina").addClass("transition-bg");

  new fullpage('#fullpage', {
    licenseKey: 'OPEN-SOURCE-GPLV3-LICENSE',
    lockAnchors: true,
    css3: true,
  	menu: '.menu',
  	anchors: ['dobrodosli', 'ginekologija', 'trudnoca', 'dojka-i-dojenje', 'pedijatrija'],
    scrollingSpeed: 1000,
    navigation: false,
    slidesNavigation: false,
    normalScrollElements: '.gineko-popup',
    scrollOverflow: false,
    afterResize:  function(width, height){
      location.reload();
    },
    afterLoad: function(){
	jQuery('.fp-table.active .aos-init').addClass('aos-animate');

	},
  	
    onLeave: function(origin, destination, direction){
      
   // jQuery('.hamburger').removeClass('is-active');
   // jQuery('.oxy-off-canvas').removeClass('oxy-off-canvas-toggled');
              
      //CIRCLE COLORS
      		var loadedSection = this;

		//ginekologija
		if(destination.index == '1' && direction =='down'){
			console.log('ginekologija dole');
          	jQuery("#krug").css("fill", "#f9d2a2");
          jQuery('.krug, .detalji').css('transform', 'rotate(90deg)');
          jQuery(".pozadina").css("background-color", "#ffe8cc");

		}
        //trudnoca
		if(destination.index == '2' && direction =='down'){
		console.log('trudnoca dole');
          jQuery("#krug").css("fill", "#efa990");
          jQuery('.krug, .detalji').css('transform', 'rotate(180deg)');
          jQuery(".pozadina").css("background-color", "#e5cfca");
		}
        //dojka i dojenje
		if(destination.index == '3' && direction =='down'){
		 console.log('dojka dole');
          jQuery("#krug").css("fill", "#a0becd");
          jQuery('.krug, .detalji').css('transform', 'rotate(270deg)');
          jQuery(".pozadina").css("background-color", "#d5dee2");
		}
        //pedijatrija
		if(destination.index == '4' && direction =='down'){
		  console.log('pedijatrija dole');
          jQuery("#krug").css("fill", "#b8c9a7");
          jQuery('.krug, .detalji').css('transform', 'rotate(360deg)');
          jQuery(".pozadina").css("background-color", "#d5ddcc");
          jQuery('#section-173-30').css('display', '0');
          jQuery( "#section-175-30" ).slideDown( "slow", function() {
            // gumbi
  			});
          jQuery( "#section-173-30" ).fadeOut( "slow", function() {
            // strelica
  			});
		}
      
      //
      //REVERSE
      //
        //dobrodosli
		if(destination.index == '0' && direction =='up'){
		console.log('dobrodosli up');
          	jQuery("#krug").css("fill", "#b8c9a7");
          jQuery('.krug, .detalji').css('transform', 'rotate(0deg)');
          jQuery(".pozadina").css("background-color", "#eae8d4");
          jQuery( "#section-175-30" ).slideUp( "fast", function() {
            // gumbi
  			});
		}
      	//ginekologija
		if(destination.index == '1' && direction =='up'){
		console.log('ginekologija up');
          	jQuery("#krug").css("fill", "#f9d2a2");
          jQuery('.krug, .detalji').css('transform', 'rotate(90deg)');
          jQuery(".pozadina").css("background-color", "#ffe8cc");
          jQuery( "#section-175-30" ).slideUp( "fast", function() {
            // gumbi
  			});
		}
        //trudnoca
		if(destination.index == '2' && direction =='up'){
		console.log('trudnoca up');
          jQuery("#krug").css("fill", "#efa990");
          jQuery('.krug, .detalji').css('transform', 'rotate(180deg)');
          jQuery(".pozadina").css("background-color", "#e5cfca");
		  jQuery( "#section-175-30" ).slideUp( "fast", function() {
            // gumbi
  			});
		}
        //dojka i dojenje
		if(destination.index == '3' && direction =='up'){
		console.log('dojka up');	
          jQuery("#krug").css("fill", "#a0becd");
          jQuery('.krug, .detalji').css('transform', 'rotate(270deg)');
          jQuery(".pozadina").css("background-color", "#d5dee2");
          jQuery( "#section-173-30" ).fadeIn( "slow", function() {
            // strelica
  			});
          jQuery( "#section-175-30" ).slideUp( "fast", function() {
            // gumbi
  			});
		}
 
	}

});
  
  
  //open popup detalji
  
  jQuery(".open-popup").click(function(){
  console.log('popup!');
  fullpage_api.setAllowScrolling(false);
});


// close popup detalji
jQuery( ".oxy-close-modal" ).on( "click tap touchstart", function() {
  fullpage_api.setAllowScrolling(true);
  console.log('popup closed');
});
  
  
  
});

//adding the action to the buttons O NAMA i KONTAKT at the bottom
jQuery(document).on('click', '.scroll-down', function(){
  fullpage_api.moveSectionDown();
});

