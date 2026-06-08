 Good morning, everyone.
 Welcome back.
 Right, so just to mention what I sent in the class email last night.
 So tomorrow, this time over at Beatrice Tinsley, we'll be doing one lecture on game theory,
 because I should be able to finish or nearly finish the power system optimisation and stuff today.
 That's usually a lot of fun.
 I'll bring a couple of boxes of chocolates to see whether you can win the game.
 I enjoyed it last year, so hopefully you do, too.
 Also, I just wanted to mention that there are questions or potentially questions on genetic algorithms
 or particle swarm optimization in the test, because we taught it in the first term this year.
 If you want an idea of what we might ask, I put the past exams here.
 Now, the university has regulations, which means we're not allowed to share the solutions to past exams.
 So what I suggest you do, if you're not clear from the lecture notes, just send me your answer,
 and I can comment on it directly.
 Right, so there's just a few questions there, just to give you an idea of the sort of things we might ask.
 Usually, it's explaining this or that.
 It will be something that was quite prominent in the lecture, not some weird detail that is easy to miss.
 Okay, so yesterday, if I can find my pens.
 Yesterday, we had a look at actually three types of problems, which I'm just quickly going to summarize now.
 Right, so with this screen, I have to try very hard to stay on the page or just yell out if I go off.
 So the first one we looked at was economic dispatch.
 So actually, for all of these problems, we're trying to solve the same thing,
 which is to minimize the cost of the generators we are going to run at any time period.
 But economic dispatch has no network constraints.
 So in the simplest case, that is simply selecting the cheapest generators to run.
 So if you were doing this, for example, for a microgrid, where there's no network constraints,
 because everything's one bus, for example, then you would be doing an economic dispatch.
 Now, of course, real power systems aren't like that.
 We have to transport power over distance.
 There's going to be a cost incurred by that.
 And we can represent that to some degree by penalty factors.
 Now, I'm aware that I explained it very badly indeed last lecture,
 so I just want to quickly mention what that is.
 So penalty factors, we calculate that value L.
 And if it's greater than one, we penalize that generator.
 So I'm going to use Li. That's a notation that we had before.
 And if it's less than one, we incentivize the use of that generator.
 And, well, the calculation of Li is based on how the losses...
 So these are the power losses in the system.
 Change as P_Gi changes.
 So this guides our solution to a solution which has lower line losses, which kind of makes sense.
 If you're running your power system well, you don't want to have too many losses.
 You want to supply loads with nearby generators.
 So we had a formula for that, not a very complicated one.
 But the main thing really is to understand what the penalty factor is doing.
 Then we went on to optimal power flow, or really AC optimal power flow.
 Okay, we derived that, and we had quite a complicated formulation here.
 I think I've already put the notes up on Learn.
 The pricing out is, of course, how we simplify this to go from the AC optimal power flow to the DC optimal power flow.
 So the AC optimal power flow was too slow because it was non-convex.
 So when you see sines and cosines, those are going to have curvature that's both positive and negative, depending where you are.
 And on top of that, those were equality constraints.
 So any type of non-linear equality constraint is going to be non-convex.
 It's going to make the problem non-convex.
 And it's very large.
 Because actually we had two equations per line, and those were equality constraints.
 We had a line limit at the bottom here, so we're going to have one inequality constraint per line.
 What else did we have?
 At each bus, we have a real and a reactive power balance, so we're going to have two inequality constraints per bus.
 We also have a voltage limit.
 And it's both ways. We have to guard against high voltage and low voltage, so there's actually two inequality constraints per bus.
 And then we have all the generation constraints as well, so it's very large.
 So to simplify that, what happens in practice is that we use what's called the DC optimal power flow.
 And this has nothing to do with the system being DC. It's just a name for the approximations we come up with.
 And we had four key simplifications.
 The first was to ignore reactive power.
 To assume the voltages were fixed, and usually one per unit.
 To assume that the angles from one bus to another are small, which gives me that the cosine of the angle is equal to one approximately,
 and the sine of an angle is approximately equal to the angle itself.
 This gives us a linear problem, which is good, as long as our cost functions are linear.
 And then lastly, we assume that there is no resistance in the lines, which means there is no conductance either.
 So when we made all of these approximations, we were able to cross out the vast majority of this.
 And at the end of the day, it gave us a simplified formulation, which kind of looks like that.
 Okay, so that's a quick recap of where we got to yesterday.
 We're just going to talk a little bit more about optimal power flow, and then we will move on to our second topic, which is state estimation.
 Right, so I think I mentioned yesterday that once you get a solution from this DC optimal power flow, you need to check that it's feasible in the original problem.
 So you just run it in a power flow and make sure that everything looks okay there.
 So that's also checking for constraints in the full AC power flow.
 Right, so there are lots of different optimal power flow types.
 I usually get asked, you know, which one do people actually use?
 And it turns out some of them are used and some of them aren't really used, but are more of a teaching tool.
 Or they're used by academics for various purposes as well.
 But in industry, the ones that are used are the security-constrained economic dispatch or, well, sometimes it's the security-constrained DC optimal power flow.
 So the equations that we used, I showed you they were being used in transpower.
 So this is being used. We use the economic dispatch itself for planning.
 Yeah.
 I think that the power flow here, which is just the steady-state solution, probably shouldn't be part of this because it's not an optimization.
 The AC optimal power flow is not used because it's too slow.
 So we showed an example and it was about 30 minutes.
 Even for New Zealand, which is a smaller network, it's too slow to be run at the moment.
 And the security-constrained optimal power flow is the slowest, but we do need to talk about what security constraints are.
 So at the end of the day, when you dispatch your power in a power system, you have to have a feasible solution.
 But you also have to satisfy what we call contingency constraints.
 So these make sure that if something happens unexpectedly, you can still run the system within limits.
 So it's like a safety margin.
 If you think about it in terms of you've got your constraints, but now we're also asking for a safety margin from those constraints, so to speak.
 And that's important because, you know, a power system is such an important piece of infrastructure.
 We don't want to run a cheap but risky operating point, which could easily be taken down by a fault.
 So the true security-constrained optimal power flow is actually orders of magnitude more expensive computationally.
 Because, actually, you need to solve the solution with a full set of constraints for every contingency.
 So for New Zealand, that would look like, okay, if the HVDC is out, can we still run the system within constraints?
 If each generator is out, if each line is out, etc.
 Now, obviously, some of those are fairly trivial and don't need to be checked.
 If the line down my street is out, well, it's too bad. It's not going to take down the system with it, right?
 But we still, for every case, in theory, have to add a full set of constraints.
 Which means that the problem that we had last time is, you know, rather than crossing out a whole lot of stuff, I need to add a full set for every single case.
 And that's a bit painful, actually, because all of these cases are going to blow up the size of our problem.
 So every new contingency, you've got a new network, therefore you need a whole new set of power flow equations and everything.
 So it's really, really hard to deal with.
 But it's also something we do kind of care about, because at the end of the day, if you dispatch slightly sub-optimally,
 you might have lost a little bit of money, but it's nothing compared to the cost of having a blackout or a partial blackout because you were running too close to some sort of security limit.
 So what usually happens is we solve the DC optimal power flow, but then we check the solution against a subset of contingencies.
 So all that happens in Transpower is that some smart engineers there have scratched their heads and they've come up with a set of contingencies that, in their experience, are the most likely constraints.
 So those include, for example, the HVDC, large generators, especially ones close to Auckland, because we can get power flow constraints there, and things like that.
 So we're just trying to check against the biggest constraints.
 But no, we don't usually manage to plug all of those as constraints in the problem.
 We're just checking the solution.
 This is not optimal, you know.
 If you've got a full set of constraints, usually you can't just delete some of them and then check against them afterwards.
 But all of this is necessary to make sure the problem can be solved in time for dispatch.
 Now, it's all well and good if your solution fits the constraints.
 We're all happy when we have an optimization problem that we simplify.
 We get some reasonable solution that's good enough, and then we check it and it's feasible.
 But if it's not feasible, then what do we need to do?
 Well, it turns out they just simply add some heuristic constraints.
 Actually, they describe what they do on their website.
 So they just add a few extra constraints in the problem and then re-solve it and then try it again and re-solve it and try again if it still doesn't work.
 But by knowledge of the system and intuition, they've got pretty useful heuristic constraints in terms of guaranteeing that the next solution,
 even though the cost is going to be worsened, will at least be feasible in the sense of these security constraints.
 So that's what happens.
 So you start by solving the DC optimal power flow.
 Then you check that against a subset of contingencies and make sure that it's got your margins.
 So for a lot of the country, we want n-1, which means that any one fault or device tripping out or line isn't going to take down the system.
 And then if our solution is not feasible, we're going to add extra constraints to be conservative,
 such as trying to run certain lines close to the maximum, those sort of things.
 Right, does that kind of make sense?
 Yep.
 So I think last year's agenda was a question just asking to explain what security constraints are.
 I'll include some links at the end of these slides so that you can read a bit more if you want to know more.
 But you only really need to know what's in here.
 So I think my key message is that as a critical system, we need to sacrifice some optimality for a solution that is safe.
 Right, so it's just like if you're on the edge of the cliff.
 You want, as good of you as possible, you would go right to the edge.
 But we kind of want to stay safe too, so we're going to stay a little bit away from the edge just in case, I don't know, we trip up or a blast of wind hits us.
 But, you know, people's safety limits vary per person, but for the power system, usually we try to be quite safe.
 Okay, so when you run this optimal power flow, you get different Lagrange multipliers, and it turns out that those can correspond to locational constraints.
 And those, I think I showed it last lecture, give locational marginal prices.
 So you can see them, for example, on EU6's live website.
 That was last lecture.
 And that's because these Lagrange multipliers, when you solve them, like we did in the example on economic dispatch, give us the units of dollars per energy, so to speak.
 Okay.
 Right, so this is one of the main uses of optimization.
 It's used to optimize dispatch, dispatch the market, and what happens basically is those solutions are sent to the generators.
 And for those who did (couse)382, then the generators can adjust that set point based on group, based on the frequency.
 So the automatic generation control would try to track that set point, but it might differ in practice slightly.
 What happens after that, actually, is that Transpower will integrate the power over the five-minute block and use that for revenue distribution.
 So even if you operate through for whatever it does, it is counted in revenue distribution.
 Okay, so the second topic is a little bit of a shorter one.
 It's talking about power system state estimation.
 So the main idea here is simply to work out a best estimate of the states, which are usually the voltages, the currents, and the power flows of the power system, based on the measurements you have.
 Now, there are different ways of doing this.
 You could do power flow, but then you might not have two measurements per bus.
 Actually, you probably don't have two measurements per bus if you've got a big system.
 Just think of the system I put up there.
 If you're going to have two measurements per bus, you needed 60-something thousand measurements.
 It's a big problem.
 If you have errors, you might end up with a non-convergent power flow.
 Some of you probably fought a bit with Aliphate if you were doing 480 and found that errors resulted in non-convergence.
 And if you're dealing with 60,000 sensors, there's probably a good chance of an error, which means that your power flow can't converge anymore.
 And actually, those power flows, it's two measurements per bus.
 What are you going to do if you've got a line flow measurement, which is quite often what you have?
 Not obvious, anyway.
 There are ways to try and incorporate it, but it is at least not obvious.
 So most power system operators have a state estimation program, and I'm just going to talk about what that optimization problem looks like.
 Just out of interest, quite a few of you are doing 403.
 Have you learnt about observers, like Lundberg observers there?
 Not yet?
 I think it is part of the course, or at least it was when I did it years and years ago.
 Those observers, were they there, Lara, or not?
 Just talk about observers in general, not like any system.
 Sure, so observers in general, like a state observer, right?
 So that's the other main competitor to the state estimator.
 They go from dynamical system theory, where as long as your system is observable, then you're able to work out what the system is going to do.
 This has advantages and disadvantages.
 The truth is those observers do require observability for those who are doing 403, whereas here we can actually fudge our way around if we don't have full observability.
 So this is what's used in industry at the moment, but a lot of research is working on both streams concurrently.
 Okay, so when we're doing state estimation, we're going to use the DC power flow equations, because they're simple and we can do examples.
 In practice, they actually can do the AC power flow equations, even though that leaves it to be non-convex.
 I think the main thing is this is not used for real-time dispatcher control, so you can do it a little bit slower, and it turns out that the problem is probably a little bit simpler.
 Okay, so we're just going to do an example. This is from the textbook I'm using for this section.
 It's freely available online, and on the last page, on my last slide, I've got a link to it if you want to learn more.
 So we're using the DC power flow model, which means that our power flows are given by this.
 So for those who are not power systems engineers, that's the power flow.
 This is the susceptance. It's a parameter you're given that the power company will know based on what's on the lines.
 And this here is the angle difference.
 So even if you aren't interested in power, it would probably be worth internalizing that power flow is based on angle differences from one part of the network to the other.
 Just that intuition is probably going to help you.
 So in this case, I've got three lines and three power flows, so my stage estimation problem is...
 Well, I've just defined all of the angles, or defined all of the power flows, so let's have a look at that.
 Stage estimation problem is defined...
 Well, really it's all the angles, that's what I want to know. Once I've got the angles, I will know all my power flows.
 Now, I have three measurements here.
 And I have... Well, actually I kind of have three unknowns, but I only have two unknowns because angles are all relative to each other.
 The only thing that matters are the angle differences, right?
 So therefore I actually have to set what's called a reference path. I'm just going to choose that as theta1, but you don't have to choose that.
 So this is reference.
 Because an angle is only meaningful if it is related to somewhere here.
 If I give you just a single vector and ask you what angle is it at, you will either compare it like we do to the horizontal line,
 or if you've got no reference for whatever, there's no angle, you need two vectors to have an angle difference between them.
 So we choose one as the reference path and then find everything with respect to that.
 Right, so we need the line parameters.
 So we have the equation B is equal to x over r squared plus x squared.
 This is a fundamental electrical engineering equation.
 So therefore I have B12. Well, there's no mention of r, so I'll assume r is zero.
 So it's going to be x over x squared, which is 1 over x, which is 5.
 B13 is equal to 2.5 and B23 is going to be equal to 4.
 OK, right, so we're just going to go through each line one by one.
 So from bus 1 to 2, I know that I've got a measurement of 62 megawatts, which is 0.62 per unit.
 We're going to use per unit for everything. It simplifies it for everyone, so 0.62.
 And we've got the equation here. It's equal to B12, which is 5.
 And then theta1 minus theta2, so theta1 after theta0 and that's going to be minus theta2.
 Let's solve for that.
 So theta2 is equal to minus 0.62 over 5, and that is equal to minus 0.124 radians.
 OK, so I've got theta2. Now for theta3, well, I'm going to do the same process.
 So theta3 is going to be equal to, let's choose this line, 0.06 per unit.
 So we're going to have 0.06 is equal to, this line is 13, so it's 2.25, 0 minus theta3,
 which gives me theta3 is equal to minus 0.06 over 2.5, which is minus 0.024 radians.
 OK, so now I've worked out all my angles, but I actually have another measurement here,
 so I just want to check that one here, so I'm going to write its equation.
 So the power flow for my flow from bus 3 to 2 here is that, is given as 0.37 per unit.
 So 0.37 is going to be equal to 4, that's my susceptance, and then it's going to be theta3,
 which is minus 0.024 minus theta2, so minus 0.124, and theta is equal to, well, 0.40.
 So it kind of is not quite equal, yep.
 So is theta3 equal to theta2?
 That's right, yes, those are good points, yep.
 So if you've got a parameter for the line that works in both directions,
 I could have just swapped the angles around and used negative, maybe that would be a bit less confusing actually.
 It's just actually the way the textbook did it, it put theta3 here and theta2 there.
 OK, so clearly there's some little mismatch, it's not too bad, but there's a little bit of a mismatch.
 So because of that, I'm not quite sure that these are correct.
 So of course I'm going to do least squares, and that's the basis of power system state estimation.
 In week 9, Professor Roy Smith will be talking a bit about least squares again,
 so I'm not actually going to labour the least squares part too much,
 I think if you're doing 403 you're doing least squares too,
 because that is like the number one optimisation application to be honest,
 but I just want to show you how it's done in the context of power systems.
 OK, so that page was for writing what I've written here.
 So if you're familiar with least squares, how many people have actually done least squares?
 Quite a lot of people.
 So you know that often we have a weight of least squares,
 because we for example trust some measurements more than others,
 that's the same in the power system, you know,
 you've got older metres which may have more inaccuracy in general,
 and you've got newer metres which have better accuracy,
 so you want to trust the better metres more,
 so we just make a weighted least squares formulation here.
 OK, so I'm just going to show you how we make the formulation,
 and get it into a standard least squares form.
 OK, so our formulation is theta1, theta2, all the way to theta n,
 and we want our theoretical prediction to match our measured prediction.
 So we're going to go to all our lines, i, j,
 the math notation would be to say it belongs to the subset of lines,
 which are for some reason often denoted as m in the literature,
 so just so you know what that means.
 When you're solving exam problems based on this,
 we're not going to be too fussy on notation, it's like that, it's not a math course,
 but you will have to formulate some of these problems,
 just to show that you can transfer words into a math formulation,
 which is kind of like what half the course is about,
 half of it is about solving it,
 but the other half is about formulating sensible optimisation problems.
 So we're going to have some sort of measurement,
 usually we do have line measurements, that's the usual thing we have,
 so i, j is going to be measured,
 and we're going to try and match that up with our theoretical model.
 These squares, usually we're trying to minimise the sum of squares error.
 Then we are going to see the bus as reference,
 if you don't see the bus as reference, I'm just going to choose 1,
 then it turns out you get infinitely many solutions,
 and the optimiser doesn't like that,
 because if you have two buses,
 zeta1 is equal to 1 and zeta2 is equal to 2 is the same as choosing 0 and 1,
 or minus 1 and 0, etc.
 So infinitely many solutions is not very good for your optimiser,
 so it's better to choose one bus, which is your choice, as reference.
 OK, right, now the standard least square form is kind of,
 I'm just going to try and do that,
 it's going to be as follows,
 x2, because I'm choosing x1 as my reference,
 all the way to xn,
 summation i to 1 to n,
 because we're just going to take each measurement,
 zi minus, this is my model,
 that's my measurement,
 and this here is how we're going to get the weights,
 I'm just going to quickly explain what...
 I've just put the geometry, what are the x's representing?
 These are our design variables in a least squares problem,
 so they're going to represent the angles.
 So, to do this conversion,
 so this is the usual least squares form,
 so I'm just relating what I've got to that,
 so to relate it I'm going to make my x's my theta,
 my z's are going to be my measurements,
 so that's bij measured,
 and that's for all the buses here.
 It's sigma squared,
 which is the standard deviation of the measurement i.
 Right, so this is our problem,
 it is clearly a least squares problem,
 I'm just taking it to the normal form here,
 and actually I'm going to take it to the vector form next,
 so what we're going to do is,
 we're going to think of everything as a vector,
 so that's going to be theta,
 from theta i, from i is equal to 2, to n,
 and this is going to be a vector as well,
 of all the measurements.
 OK, what about my function f?
 Well, that is the model I'm fitting to,
 in a usual least squares form,
 in this case my model f is going to be f of x,
 it's just going to be all of these equations,
 which I can actually represent as a matrix,
 times my vector here,
 so this is equal to bij beta,
 for all lines in matrix form.
 So remember our x's are our thetas,
 so the thetas occur here,
 the h's are going to,
 I'll actually show an example where we actually construct the h's deliberately.
 OK, so if I've done this,
 I can, well, put it into matrix form,
 which will let me get a solution,
 a general solution easier,
 that's one of the main reasons we don't need to vector matrix form,
 so I can just get the general solution.
 I think there's one more matrix I need to mention,
 which is going to be, we're going to define an R matrix,
 this is the weighting matrix,
 and it's going to be a diagonal matrix,
 of these standard deviations squared.
 OK, so once I've done this,
 I'm going to get,
 min of x,
 z measured,
 minus f of x,
 the whole thing transposed,
 R minus 1,
 z measured,
 minus f of x.
 So this is just your standard,
 bog standard,
 least squares problem.
 I will put this up on noon after the lecture, of course,
 so don't worry if you're getting a bit behind.
 Right, so I know that f of x is equal to h times x,
 so I'm just going to re-substitute that,
 and then expand it out,
 which gives me min x,
 optimization problem is equal to,
 the following,
 so we're just actually,
 using the distribution principle to multiply this thing out,
 everything,
 the model is linear, so we can do that.
 x, t, h, t,
 so this comes from replacing f of x with h, x,
 and then taking its transpose,
 h, x, transpose,
 is equal to x transpose, h transpose.
 Don't worry about remembering all of these identities,
 you're not going to need them for the exam.
 I want you to understand how the process works,
 and to be able to formulate simple problems yourself.
 R minus 1, z measured,
 and then I'm going to get z measured,
 transpose, r minus 1, h, x,
 and I'm going to get plus,
 x transpose, h transpose, r minus 1, h, x.
 Now, for those of you who haven't done math for a while,
 I just want to remind you that x and z measured are column vectors,
 which is absolutely standard for least squares,
 because we tend to use column vectors there.
 Okay, so all of this function,
 all of this here, this thing here,
 can be considered as a cost function,
 J of x,
 and the solution, of course, is given by,
 well, the gradient of that is equal to zero.
 It's an unconstrained problem,
 so we can use the techniques Lerr talked about,
 but actually, this is a standard form,
 so it's got a closed form solution,
 so we can solve it analytically.
 That gradient gives us minus 2, h transpose,
 r inverse, z measured,
 plus 2, h transpose, r minus 1, h, x.
 So that's the gradient,
 and I can,
 I can then find my optimal x, x star,
 so if it's x star, then this thing's going to be zero.
 It's going to be,
 h transpose, r inverse, h minus 1,
 h transpose, r minus 1, z measured.
 And this is the standard form of a least squares solution.
 One of the reasons we like least squares so much
 is that we don't actually need to run one of Lerr's
 unconstrained optimisation algorithms to find our solution.
 We just get it immediately from the master.
 So this is just standard linear least squares.
 You do not need to be able to repeat the derivation yourself.
 All I want you to know is you can formulate it as a least squares problem
 and then look up what the solution looks like directly
 because this is a well-known result.
 So you just need to, if you go back here,
 put your design variables into x,
 and then your measurements into z,
 compare what the model says and your measurements,
 and then minimise the squared error,
 and then you get the solution immediately.
 Okay, so this will be up on Lerr after the lecture.
 Are we assuming h is squared?
 It won't necessarily be squared, no.
 It just depends how many measurements we have
 versus design variables we have.
 So quite often it's actually non-squared.
 And that is kind of the next thing I'm going to go onto right now.
 So it's a very good question.
 So sometimes...
 So sometimes we have a different number of measurements
 to design variables,
 which means that our h matrix is non-square.
 So that was literally the very next thing we were going to talk about.
 Now, if we have less measurements than design variables,
 what we can do is try to find an estimated value for x
 such that the sum of squares of x is minimised.
 So this is what happens in least squares.
 Then you get a different closed form solution here.
 I'm not going to go through the math,
 but you can do it yourself if you want an exercise.
 To be honest, that might be useful for Roy's part of the course.
 It won't be too useful for the power system part of the course
 to go through there.
 Now, so these are the...
 This is just a summary of what we can have.
 We can have an under-determined problem.
 That means not enough measurements.
 And then you can kind of do that...
 Try to find a vector that minimises the sum of squares.
 You can have a completely determined problem,
 but most of the time we have an over-determined problem.
 So I don't know why the table didn't put that there.
 So over-determined means that we have more measurements than we need
 and then we can do a least squares fit.
 That's the usual case with least squares.
 Usually with least squares we have more measurements than we need
 and we're trying to find the best approximation between it.
 Quite often least squares are kind of drawn as fitting to data.
 Let me just draw some data here.
 If you only had two points,
 you could just draw a line straight through.
 That would be completely determined.
 But if you've got lots of points,
 you're going to be trying to find some sort of best fit line like that.
 That's all least squares is.
 It's the same as what we're doing here.
 Now, in power system state estimation,
 we don't actually solve under-determined problems.
 It's not very numerically robust what we're doing there
 and just that minimising the sum of squares
 has no basis in power systems reality.
 So what we usually do is we add extra measurements,
 which we call pseudo-measurements,
 to the measurement set so that we have
 at least a completely determined or possibly an over-determined problem.
 In the 1970s and 80s,
 that happened by the system operator getting on the phone
 and ringing up the generator and asking for some of the measurements
 right then and there and then putting it into the program.
 Nowadays, it's based on historical or previous measurements,
 so you're adding them on at the moment.
 If we're doing that,
 we're going to assign a large standard deviation
 because we don't have that much confidence in this measurement
 because it's an old measurement or something.
 But it's better than not knowing anything.
 OK, so I have another example,
 but I don't have a great deal of time here,
 but I do kind of want to do what I can here.
 So the textbook has a lot of different examples
 where we change the metre accuracies
 and see how the solution changes,
 but I just want to actually discuss this problem first.
 So it's the same network as before,
 same parameters, same everything,
 but we've got a little bit of a new thing here.
 So the metre accuracy is plus minus three megawatts,
 so that is kind of about three standard deviations.
 So therefore we're going to say that
 sigma is approximately one megawatt,
 which is equal to 0.01 per unit.
 Right, so now let's start with my H matrix.
 OK, because remember I'm going to be solving,
 trying to minimise that square of Z measured minus F of X,
 so I need to work out what F of X equals to H X.
 What is this H?
 Sorry, that should just be X there.
 So H is going to be something like this.
 You've got three angles that we don't know.
 Now we're actually going to flux one of them to zero,
 and the first measurement is the power flow from one to two,
 so it's going to be, the model was V12 theta one minus theta two,
 and this value was five.
 We did that before, so it's just going to be five minus five and zero.
 The second equation we have in our model,
 so this is just putting the model equations in,
 theta one minus theta three,
 and the value we had been given here was 2.5.
 We did those B calculations last time.
 2.50 minus 2.5,
 and lastly we have B,
 I'm going to put it 32,
 and that was going to be theta three minus theta two,
 and the value here was four.
 So that is going to give me four and minus four and zero.
 So that's my H.
 Now, remember we're choosing one of these to be zero.
 To match the textbook, I'm going to choose this one here is equal to zero.
 For some reason, the textbook switches from using theta one and theta three as the reference.
 It does not matter what your reference is.
 If we do that, then we can ignore this because it always multiplies zero.
 Right, our formula also had R.
 We can put R in as well.
 We know our sigma is about 0.01,
 so R is going to be equal to ten to the minus four,
 ten to the minus four, ten to the minus four,
 because ten to the minus four is sigma squared.
 So this is ten to the minus two,
 so square it, you get ten to the minus four.
 Okay, so as long as I've got my H and my R,
 I have my Z measurement.
 You can't quite see it up here,
 but this gives me Z measured as simply 0.62, 0.06, 0.37.
 It's an over-determined problem because I only need to find two things,
 and I have three measurements,
 so I just plug it into the formula for the over-determined case,
 and hey presto, I get my solution,
 which in this case, just try to stay on the page,
 is theta one.
 This means the optimal value, as you know from the rest of the course,
 is equal to 0.0285 and minus 0.093.
 And if you actually do the transformations to check against the original solution,
 you'll see it's quite close, but it's not exactly the same.
 So this is my least square solution to the problem that we posed earlier.
 Does this make sense?
 Kind of?
 Sort of?
 Okay, so...
 Can you also show us the construction of H?
 Sure. So H is a system model.
 It's saying that given my design variables,
 what measurements would I expect to see?
 In this case, my system model are these power flows,
 because I'm relating the measured power flow to the model.
 The model we're using is just those DC power flow equations that we had before.
 So if you just multiply...
 Sorry, maybe I forgot to put X here.
 H times X. So the H is this part, and the X is that part.
 I think that's how we...
 That's the matrix equation, isn't it?
 Exactly, yeah.
 In reality, we'd probably use the AC power flow equations,
 but then I can't solve it quite so easily with least squares.
 But the computer hopefully can deal with that.
 Okay, so...
 Quite often you're formulating these problems.
 I would expect you to know how to construct the H and R matrices, though.
 It's least squares.
 You need that for Roy's part of the course as well.
 Okay, so my timing is good for once.
 So I did actually want to show you how all of these things fit together.
 And also talk about how this area is developing.
 So we're getting more measurements in.
 We've got phasor measurement units, PMUs, if you've worked in industry.
 Which is good for improving state estimation accuracy.
 But on the other hand, state estimation, if you look here...
 Did we worry about what the load was doing?
 No, we didn't worry about what the load was doing.
 Did we worry about how things changed over time?
 No, we didn't think about how things changed over time.
 And those things are becoming increasingly important.
 If you want to avoid things like the Iberian Peninsula blackout,
 well, you kind of need to know how your network is going to change in time.
 And the effect of loads and the effect of, for example, solar and wind generation as well.
 So the state estimation problem is getting harder,
 but we are getting more tools, so to speak, to deal with that.
 In terms of more advanced topics,
 people are always trying to figure out how to cope without enough measurements
 or to detect and remove bad data.
 Because the truth is, if you get one really bad data here,
 let's say someone forgot to put the dot in and you got 62 per unit,
 it would give you complete garbage for the solution.
 And even if you had a bigger network, the fact is,
 these squares without some sort of data cleaning is likely to be quite poor.
 So that's another thing to bear in mind.
 Right, so we've discussed quite a lot of things.
 I just want to show you how that actually works.
 So the system operator has a state estimator that tells them what's happening.
 That state estimator is used to guide the optimal power flows
 because then we can, for example, substitute our voltages in the DC power flow
 with the state estimator's voltages.
 That's still a linear problem because they are constant.
 Then we have all of these different calculations.
 There's economic dispatch, which is mainly used for planning.
 Participation factors.
 You know, if you go to a lot of our generators,
 there are multiple ones in parallel, like a Manifory and so forth.
 So you don't have just one generator,
 but you actually have a whole lot of them in parallel.
 So it's how much of the base power they have to contribute.
 So if there's eight of them and they're all the same,
 you'll be doing an eighth there.

 Now, the solution that's actually sent to the generator
 is the security-constrained DC optimal power flow.
 That's the one that goes to the generator
 and is the set point for, like, the droopers we talked about in 382,
 with possible changes for the participation factor,
 because you'll be given a set point for the whole power plant,
 this whole station like Manipuri or Benmore,
 and each generator takes a certain percentage of that.

 Okay, so that's my time.
 Some resources if you want to learn more about these kind of things.
 If you're interested to talk further, just come to me.
 In terms of exam preparation, I would say just do the past exam papers.
 I will probably schedule some sort of tutorial closer to the time
 where we will just go through.
 This part is not very hard, I would say,
 but it's a bit challenging if you haven't done power systems before
 because some of the intuition might not be there.
 So in that case, do all the problems and come and see me
 if you have problems because I'm more than happy to talk through some of these things.
 Okay, so I hope to see you tomorrow.
 Most fun lecture routes, of course, in my view,
 so please do come.
 Thank you.

 That's right, exactly, that's correct.
 5 times theta 1 minus 5 times theta 2 there.
 That's the solution, so we got that.
 If you don't mind me just scrolling.
 You get it simply by plugging H and R and your measurements into here,
 and that will give you those thetas directly.
 So Z is here, R is there, and H is the first part of that.
 You use that equation here, yep, this one here.
 That's right, yep.

 You know that because you've got three measurements
 and only two design variables,
 so you're in the first case here.
 That's right.
 So all you need to do is calculate H, calculate R,
 and you're usually given Z measured straight away from the data here.
 So once you've calculated those three things, you're good to go.

 If you choose this one as zero, is it random?
 Free choice.
 Yeah, so it doesn't matter at all which one you choose.

 So you calculate R and Z is given.
 Z is given.
 You just calculate.
 So you only need H and R, that's all.
 R is not given.
 From sigma being 0.01,
 because as I mentioned, 0.01, that's sigma, yep.
 That's right, yep.
 So as I mentioned, accuracy of three megawatts,
 that's like 99%, so it's about, yeah.
 Typically I'd probably give you the sigma anyway,
 so you just need to remember to.
 It's given, this is given.
 So everything's given, you just need to calculate H, R
 and then work out the formula.

 So the way this works here is that
 that metre accuracy corresponds to sigma being 0.01.
 The definition of R is all the sigmas squared.
 So if you have 0.01 squared,
 you get 10 to the minus 4.
 Does that make sense?
 Yes, thank you.
 The sigma will be given there.
 Yeah, I'll typically give you the sigma,
 because I can't remember all the standard deviations offhand and stuff.

 I have some questions about your tutorial discussion question thingies.
 Oh, yes.
 But I'm not sure.
 You said you have time, like, 1 to 2pm,
 but there's also 382 students.
 Yes.
 So I was wondering if there's...
 Yes, yes.
 Let me just make another time for you,
 so that you don't clash with...
 Yeah, I feel like I've got a couple.
