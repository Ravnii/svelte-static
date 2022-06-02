<script>
	import { Col, Row, Container } from 'sveltestrap';
	import Header from './Components/Header.svelte';
	import Calendar from './Components/Calendar.svelte';
	import MessageBoard from './Components/MessageBoard.svelte';
</script>

<Container xl>
	<Row><Header/></Row>

	<Row>
		<Col xs="9">
			<Calendar/>
		</Col>
		<Col xs="3">
			<MessageBoard/>
		</Col>
	</Row>
</Container>
