ROTimer
==================

ROTimer allows for simple time-based loop execution and delays. By utilizing ROTimer, a certain portion of code can be run at a specific speed (processor time permitting) or "ready'd" for execution. ::



	ROTimer step1;
	ROTimer step2;
	ROTimer step3;
	ROTimer repeatingLoop;


	void setup() {
		step1.queue(0);
		repeatingLoop.queue(0);
	}


	void loop() {
		if (step1.ready()) {
			// do something
			step2.queue(1000);
		}
		if (step2.ready()) {
			// do something else
			step3.queue(2000);
		}
		if (step3.ready()) {
			// last step of the process, now repeat
			step1.queue(0);
		}

		if (repeatingLoop.ready()) {
			// do something every 1000ms
			repeatingLoop.queue(1000);
		}
	}