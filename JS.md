# Loop_Merge_Scoring
//Code to allow "enter" key for response submission

Qualtrics.SurveyEngine.addOnload(function()
{
	var qid = this.questionId;
	document.onkeydown = function(event) {
		console.log('keydown',event);
		if (event.which == 37) {
			event.preventDefault();
			Qualtrics.SurveyEngine.registry[qid].setChoiceValue(1, true);
		} else if (event.which == 39) {
			event.preventDefault();
			Qualtrics.SurveyEngine.registry[qid].setChoiceValue(2, true);
		} else if (event.which == 13) {
			event.preventDefault();
			jQuery('#NextButton').click();
		}
	}

});

Qualtrics.SurveyEngine.addOnReady(function()
{
	/*Place your JavaScript here to run when the page is fully displayed*/

});

var EndLoop = "${e://Field/EndLoop}";

Qualtrics.SurveyEngine.addOnPageSubmit(function()
{
	// code for scoring
	correctNum = Qualtrics.SurveyEngine.getEmbeddedData('correctNum');
	var input = $(this.questionId).select('.InputText');
	var answer = input[0].value;
	var solution = "$lm://Field/3}";
	if (answer == solution) {
		correctNum ++;
	}

});
