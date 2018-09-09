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
{% for event in site.posts %}
{% if event.layout == "event" %}
	{
		"title":"{{event.title}}",
		"start": "{{event.event_start |date_to_xmlschema}}",
		"end": "{{event.event_end | date_to_xmlschema }}",
		"url":"{{site.url}}{{event.url}}"
	}
	{%unless forloop.last %},{%endunless%}
{% endif %}
{% endfor %}
],
    timezone: 'UTC',
    timeFormat: 'H(:mm)',
    header: {
  left:   'title',
  center: 'month,agendaWeek,agendaDay',
  right:  'today prev,next'
}
	})

});

</script>

<div style="padding-top: 10px;" id="calendar"></div>
