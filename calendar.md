---
layout: default
title: "Events"
permalink: /calendar/
---

<script src="https://code.jquery.com/jquery-3.1.1.min.js"></script>
<script type="text/javascript" src="/scripts/moment.min.js"></script>
<script src="//cdnjs.cloudflare.com/ajax/libs/fullcalendar/3.2.0/fullcalendar.min.js"></script>
<link rel="stylesheet" href="//cdnjs.cloudflare.com/ajax/libs/fullcalendar/3.2.0/fullcalendar.min.css">
<link rel="stylesheet" media="print" href="//cdnjs.cloudflare.com/ajax/libs/fullcalendar/3.2.0/fullcalendar.print.css">

<script>

$(document).ready(function() {

	$('#calendar').fullCalendar({
		events:
[
{
		"title":"padding",
		"start": "0",
		"end": "1"
}
{% for event in site.posts %}
{% if event.layout == "event" %}
	,{
		"title":"{{event.title}}",
		"start": "{{ event.event_start | date_to_xmlschema }}",
		"end": "{{ event.event_end | date_to_xmlschema }}",
		"url":"{{site.url}}{{event.url}}"
	}
{% endif %}
{% endfor%}
{% for eventt in site.ex_events %}
	,{
		"title":"{{eventt.title}}",
		"start": "{{ eventt.event_start | date_to_xmlschema }}",
		"end": "{{ eventt.event_end | date_to_xmlschema }}",
		"url":"{{eventt.event_url}}"
	}
{% endfor%}
],
    timezone: 'UTC',
    timeFormat: 'H:mm',
    defaultView: 'listMonth',
    header: {
  left:   'title',
  center: 'month,agendaWeek,listMonth',
  right:  'today prev,next'
}
	})

if ($(window).width() < 960) {
  $('#calendar').fullCalendar('option', 'aspectRatio', 0.8);
}
if ($(window).width() > 960) {
  $('#calendar').fullCalendar('option', 'aspectRatio', 1.35);
}

});

</script>

<div style="padding-top: 10px; height: 80vh;" id="calendar"></div>
