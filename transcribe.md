 Good afternoon, kia ora koutou, good to see you all, welcome back, thank you for coming,
 I think this is a busy week for many of you, and of course we have our test on Friday as
 well, so what my plan is for the next three lectures is we do have to teach new material
 for the exam, that's just the way it is, but I'm hoping that you can understand as we go
 along so that you don't have too many unanswered questions swirling about, so if there's something
 you don't understand, please do put your hand up so that you can finish this lecture, know
 the material, and yes you'll have to do some practice, but not more than that.
 OK, so this week is about power systems optimisation, actually though I usually only need two lectures,
 sometimes two and a half of that, so on Wednesday what we're going to do is do a lecture on
 game theory, which is one of the other topics I have to teach, this is kind of just a fun
 lecture, we can make time for some questions about the test as well if that's helpful,
 and I will announce details shortly on Learn, but we usually offer a couple of boxes of
 chocolates to whoever wins the game, because we play a couple of games as a class to illustrate
 the lecture material, so usually we run the game twice and there should be two winners,
 and we'll see who gets that, so try and come on Wednesday if you can, mainly because it's
 fun, and it won't, hopefully won't be too difficult to understand at the time.
 OK, so the idea here is how is optimisation used in power systems, quite a lot of you
 are doing power, not everyone, if you're not interested in power that's completely OK,
 just treat it as an example of how optimisation is used in one industry. Actually we will
 talk about optimisation applications to a lot of different things, and part of becoming
 a good optimisation engineer is getting an idea of how to apply optimisation to lots
 of different things. So just a quick overview of what's going to happen, so this week is
 week 7, this is going to be me, and it's going to be pal with a little bit of game theory,
 mainly because I love playing the game, so I had to put it in somewhere. Week 8, that's
 going to be Leah. Week 9 and 10, this is going to be Roy, Professor Roy Smith from ETH Zurich

 is coming to teach two weeks. The topics I think are least squares, which you probably
 already some of you get in 403, but it will be good to hear it from a different perspective,
 and then robust control and distributed optimisation, so there's a lot of very interesting things
 there, all closely related to optimisation. Then week 11, it's likely to be Lou again,
 and then 12 will be the presentations. I will send an email out probably later this
 evening, just to give a bit of a road map. Okay, so when I developed this material, I
 sort of had a little bit of a brainstorm, and how do we use optimisation in power systems?
 So there's probably two main traditional applications of optimisation into power systems,
 and the first one is economic dispatch or optimal power flow, and this is just simply
 answering the question of how much power should each generator supply? So for those of you
 who are doing 480, right, you've got this load flow that's based on the powers from
 the generators, but how do you know that those generator set points are any good? I bet there's
 a few times you want to sort of adjust them to avoid getting issues. So optimisation or
 optimal power flow is about sorting out how much power each generator should give so that
 your network runs properly. Then we have power system state estimation, we'll do that tomorrow,
 and this is about visibility, so that you can see the voltages and the currents for
 your network, because at the end of the day, if you remember 382 or even probably 480 as
 well, you've got those power flow equations, right? There's four unknowns per bus, and
 you've got two equations, so you need to know two things, that might be the real and reactive
 power, or the power and the voltage, etc. I think we'll go through that in 382, which
 many of you have done. Well, the truth is, often you don't quite have enough sensors
 to do that, so then you can use a state estimation programme rather than trying to solve the
 power flow directly. Another big application is load forecasting. So it's very useful to
 system operators to know what the load is going to do. They can get down to maybe 1
 or 2% error for New Zealand. I think it was about 15 years ago now, Transpower did a trial
 and updated their load forecaster. So it's a very simple problem, it's asking someone
 to write a programme that takes all the past data, weather data and so forth, to figure
 out how much load do we think is going to occur in the next half hour or the half hour
 after that, and so forth and so forth. So, yeah, I worked a bit on that project. Now,
 in the power system there's now a lot of power electronics, and when they get to be really
 big power electronics, such as, for example, modern high voltage DC links, ours are probably
 older technology so they don't really do this, then it becomes important to do some sort
 So that's when you get, like, model predictive control like we learnt last term. And then
 there's scheduling and so forth, energy management, that's sort of what our assignment is based
 on if you're doing that one. Okay, right, so we're going to just go through the problems
 one by one. If you don't understand anything, really do shout out. So, economic dispatch,

 this is talking about how we can meet the demand as cheaply as possible. So the key
 aspect of the economic dispatch problem is it doesn't consider any network flows or losses
 or constraints. So this is saying, what is the cheapest generation I have on offer? So
 if you are the system operator, all the generators will submit bids to you in advance, saying
 that, okay, I can produce so many megawatts for such a price, and you have to decide which
 one to take. Okay, so having said that, we will talk a little bit later about penalty
 factors, which is how we get realistic solutions out of economic dispatch. For example, if
 I have a big load in Southland, for example, it probably doesn't make sense to dispatch
 something in Northland to supply that. So we need some way to cope with that, because
 then I'd have to transfer the power all the way through the network. Okay, so the formulation
 here is very, very simple. So we're simply going to minimize some sort of cost. Usually
 it's a cost at each generator, so we're just going to sum through all the generators and
 their cost functions. And the decision variable, of course, is all of the generators. I'm just

 going to explain a bit of notation while I'm here. This is the active power. So for those
 who are not power systems engineers, we have active power and reactive power. Active power
 is what we're talking about here. If you're curious about it, you probably don't need
 it for this course, but it's probably worth it just in general just to read up a little
 bit about what reactive power is. So that's of each generator i. This is our cost function.

 Cost function. And quite often it is simply a price times, that's a multiplication, right?
 So the generators usually submit how many cents per megawatt hour they want to be paid
 for to run these generators. Right, now in terms of constraints, we're going to have

 each generator within its limits. So the bar notation denotes the maximum and the minimum.
 I'm just going to put that in, that's the max and that's the min. And we need that the
 sum of the power generated is going to be equal to our total system demand. Right, so
 it's simple. I just need to get generation to supply my demand. Everyone's good with
 this, right? Yep. Okay, right. Now, of course this is an optimization problem. Actually
 it's got equality and inequality constraints. I could solve it with KKT conditions, Lagrange
 multipliers and so forth. But the truth is, quite often you can do it simpler than that.
 And if you are submitting bids at a particular cost, well, we know without even doing any

 theory what to do, take the cheapest ones. So that's in fact exactly what happens. We
 simply take the cheapest ones. It's called merit order, but I think everyone understands

 how that works. You simply select all the cheapest bids until you have enough power.
 So you ignore expensive generators and keep using cheap generators. Quite often these
 generators, it's actually the same generator having different price points. Costs are often
 a little bit non-linear, so they will give multiple bids. Like I can operate at a low
 power for a cheap price or a high power at an expensive price, and that's what we see
 with multiple bids. So you accept everything up to the demand and nothing further than
 that. Just as a general note when doing optimization problems, just because you can do KKT conditions
 doesn't mean you should do KKT conditions. If there's any way to simplify the problem
 or see the solution instantly, that's often better, and this is a little bit of a clue.
 The test may include an example that is worth thinking outside the box rather than just
 diving in with loads and loads of math.
 Okay, so we're actually going to do that though. We're going to do it the proper way here for
 now. One common question I get asked is, oh, does the power system question in the exam
 use Term 1 material? And it kind of does because you do need to be able to solve constrained
 optimization problems and understand how some of the algorithms we talked about work.
 Okay, so what we're going to do is, well, I think we're going to solve it properly.
 It's a good preparation for the test because, you know, KKT is definitely something there.
 So we're going to formulate the Lagrangian, PG1. So these PGs, they're my decision variables.

 In the first part of the course, we would have called them the X1, X2.
 Okay, right. What sort of constraints do I have? Well, I've got one here.
 It is an equality constraint, so I'm going to use a lambda for that.
 Now, the economic dispatch considers both costs. We're trying to minimize system costs.
 That's the one thing about all of these economic dispatch, optimal power flow things.
 We're always trying to minimize the system cost. It's not run by any generator.
 It's run by the system operator to try and find the best way of running their system.
 Okay, so we're going to have everything in the cost function.
 So I'm going to just replicate that.
 And, of course, I have the constraints going in there. So that's my Lagrangian.

 I actually need to get this into the correct form, because remember our equality constraints should be that something is equal to zero.
 So that is 500 minus PG1 minus PG2 is equal to zero. So that's the equality constraint there.
 Okay, now I'm going to take partial derivatives with respect to each design variable.
 And that gives me, well, the constant drops off. 20 plus 0.02 PG1, and then I've got a term here.
 Minus lambda is equal to zero. That's a G, sorry. Just bad writing.
 15, so we're just taking partial derivatives of this.
 Plus 0.06 PG2 minus lambda is equal to zero.
 And then the last condition is 500 minus PG1 minus PG2 is equal to zero.
 Right, so now I've got three equations and three unknowns. It's a linear system, so I can solve it.
 I trust you can solve linear equations, so I'm just going to go straight to the answer.
 So we're going to have PG1 is equal to 312.5, and that is megawatts.
 PG2 is equal to 187.5, and that is megawatts.
 And lambda is equal to 26.2. Anyone know or guess what the units for this would be?
 So it's actually dollars per megawatt.
 And if you ran it for a certain time period, like a half hour or an hour as implied here, then that would actually be an energy cost.
 So actually, even in the New Zealand electricity market, the Lagrange multipliers correspond to the price.
 So if you go, let me switch to the computer here.
 So this looks at the New Zealand electricity market. You see you've got slightly different prices at the moment.
 These are dollars per megawatt hour, depending on location.
 That's a mixture of how much supply and demand there is kind of at that location.
 And those actually correspond to the Lagrange multipliers of the optimal power flow problem.
 So they're actually based in optimization at the end of the day.
 So, for example, if you look at Auckland's price history, when they're struggling to get power up to there, the price is going to peak quite a lot.
 OK, right, so that's just a simple example of economic dispatch. I'm hoping everyone's good with that. It's not too bad, right?
 Would you check through the machine checks?
 Technically, yes, but if you notice that the cost functions are quadratics and convex, you don't need to worry about that as well.
 But if you just get nonlinear constraints and stuff, then you should do the Hessian.
 Good question, though, thank you.
 OK, so I've done that in one page.
 Now, the problem we just looked at doesn't care about location in the slightest.
 Roughly speaking, we want to use generators that are close to the load and not far away.
 There's a good reason for that, because if we have to transfer power across the network, we're going to incur higher losses, and that's a bad thing.
 So when doing an economic dispatch, we usually want to include the impact of losses.
 And we do that by noticing that the loss is actually, well, it's a change in demand, because if we lose more power, we're going to have to supply more power to make up for it.
 So every time we send electricity through a wire, we're going to incur losses, right? I squared R.

 So we're going to put a loss term in here.
 OK, so that's just what we had before, the two cost functions for our example, and then the power balance, but now we're putting a loss term in there.
 OK, so working from that, then we take partial derivatives again, and we get this factor here.
 What is this factor?
 Well, previously, when we didn't have the loss term, this term here dropped out, and we just had lambda times one.
 That was what our function was before, if you remember our solution to the previous example here.
 You see that this lambda was just at the end there.
 But now we've got an extra factor here, and the whole thing here is called a penalty factor.
 So this penalty factor, it looks at how the losses change incrementally with a change in generation.
 This is a partial derivative. How much do my losses change based on my generation?
 And then we're going to have a penalty factor on that, which makes the generation look more or less expensive.
 OK, so we're going to solve all of these equations. You will not be able to repeat the derivation, although I think a lot of you would be able to do so.
 And you get, well, this is your Lagrange multiplier.
 Previously, your Lagrange multiplier would have been your own cost.
 This is your own cost, or really your own marginal cost.
 Marginal cost means how much does it cost to make a little increase in generation in terms of the rate my cost is increasing.
 And this here is the penalty factor here.
 What are you referring to when you talk about yourself, like your own cost?
 Sure. So each generator is going to have some sort of cost function like this, which is our generation, and this is my cost.

 And usually it follows some sort of shape there. If you're just operating at a fixed cost, then it could be flat.
 A lot of renewable generators just want to send whatever they've got out.
 But often it's a price times the amount you're sending, which means it's just a line.
 But quadratic terms are quite common too, because you don't actually want to operate near your maximum for too long because of the maintenance cost on your generator.
 So the marginal cost is actually the slope here.
 So when economists talk about the New Zealand power system, and they talk about the price being the marginal cost of the most expensive generator we have to run.
 So actually if you're a generator in New Zealand, even if it's a hydro generator, it's good for you economically if more expensive generators such as gas come in,

 because that means the marginal price is more likely to be higher and you get paid the market price, which is the marginal cost.
 So there is actually a bit of self-interest in that, looking at what other people come in.
 Right, so what is this penalty factor doing?
 Well, the penalty factor here, this thing here, is going to be less than 1.
 So let's just say that Li is going to be, well I think in this example Li is actually greater than 1, so I'll do it around that way.
 What it does is it makes that generator appear more expensive.
 And if, for example, as we'll see for the example I'll give, it's less than 1, it makes that generator look less expensive, and that's all because of the impact on losses.
 So the condition for optimal dispatch is usually, if we ignore penalty factors, that the marginal cost of all the generators we are using is the same.
 Because if they're not the same, any expensive generator should be reduced and everyone else should take up the slack.

 So actually for this particular problem we get a unique case where having all our Lagrange multipliers is the same,
 for each generator is going to, sorry, having one Lagrange multiplier, which is referred to each generator by a penalty factor of 1,
 because we're not using the penalty factor at optimum, i.e. the marginal cost, I'm sorry I did not explain that well,

 but the marginal cost at each generator is usually the same.
 But if we have a penalty factor that takes into account the losses to make up for different locations.
 Okay, right. So then, this is just explaining what I was trying to talk about. It's probably better than what I said,

 but the point is, we can make a generator appear more expensive or more penalised,

 and that's based on how the losses change as we increment that generator's power.
 Okay, now, how do you know how the losses change?
 It's quite hard, actually. You know, if I give you a power system, even if it's a very small power system,

 how do you know how the losses change?
 Well, it's quite hard to do so by hand, but what we can just do is run a power flow.

 A lot of commercial programs will do that, and just see how the losses change numerically.

 So I just increment one generator slightly and see how the losses change, and that is actually what is done.
 So, for example, this example that we've got here, so we've got simply a two-bus system. The load is here,
 so anyone can tell me which bus should be preferred in terms of the penalty factor,
 do we want to supply the load more from bus 2 or bus 1, assuming we've got some line losses there?
 Bus 2, because it's close.
 So, if we do the power flow calculation, what we're going to do is increment the generation slightly here,
 in this case by changing it by 10 megawatts, and this one is going to have to go down by 10 megawatts,
 and then just simply calculate the change in losses there, over the change in power,
 and that's going to give us an estimate of that penalty factor.
 So this is from a power flow.
 If you are doing power and don't know how power flow works, that's OK, you don't need to know that for this course,
 but if you do work out the power flow equations, and do the math, then you would get a partial derivative.
 So you simply plug these numbers into the power flow equations, and then take partial derivatives.
 You can do it as an exercise if you want, I don't really recommend doing it,
 unless you've got plenty of time to get into the math, and then you get 0.9628.

 So it's a good approximation of the true penalty factor.
 So this is actually how economic dispatch works in principle.
 We don't want to just do a pure dispatch that's unaffected by location,
 but we can calculate penalty factors just from running power flows.
 Does that kind of make sense?
 Yep.
 OK, right.
 So we calculate that Lagrange multiplier.
 We also go through the merit order, so to speak, if we need to, and we get a marginal cost,

 either with or without penalty factors.
 So there's two ways to apply it.
 One way is uniform price pricing, where everyone is paid the market price.
 That's what happens in New Zealand.
 And, or you can pay exactly as you bid.
 So if you bid something low, you'll only get paid less.
 So if I just go back to my previous slide, this one here.
 What are you going to, let's say we accept this bid here.
 Are we going to pay the generator the market price, or are we going to pay the lower price?

 So over in the UK, it's basically the only country that I know of that does it this way.
 They say, OK, you get paid as you bid.
 In New Zealand we say that, OK, everyone gets the market price because we all supply the same thing.
 Now, on the face of it, it might seem to make sense to reduce cost to pay-as-bid.

 But you know the problem is, everyone is going to try and guess the marginal price
 because you don't want to put your real costs in, especially if they're low, because then you'll only get paid very low.
 So what we find is that what they found over there is that cheap generators are trying to bid the marginal price,
 which sometimes results in them overshooting it and more expensive generators, such as your gas for example,
 having to run even though you had cheaper energy available.
 So that's why we do what we do.
 The UK government has actually commissioned a lot of research trying to prove that their way is best.
 But most of the world does it our way, which is everyone is paid exactly the same.
 This is probably the main topic I want to talk about. It's the optimal power flow problem.
 So this economic dispatch thing, basically we're selecting cheaper generators,
 except for we might twiddle it a little bit based on that penalty factor thing.
 But of course, if you're running the system, you can't operate like that.
 You might overload lines. That penalty factor thing didn't take into account overloads.
 And therefore your solution might not actually work in the real power system.
 And that's what optimal power flow is about.
 It's about having a proper model of the whole power system, which we have,
 and then meeting the demand at the minimal cost.
 Okay, so now we're going to have a lot more constraints.
 We don't just need to deal with some power balance over the whole system,
 but we need all of those power flow equations to be satisfied.
 So actually, they will appear as constraints.
 So I think at this stage, what I'm going to do is just show you the formulation.
 But I do want to point out that if you have no system constraints,
 then you just get an economic dispatch.
 So the difference is that we've got power flow equations.
 Okay, right.
 So first we're still going to be minimizing costs.
 Now, last time I used the notation i,

 but I want to use the notation i for buses this time,

 so I'm going to switch to using G.
 I'm going to use that it belongs to the set of generators.
 So I'm just going to write down that that's a generator,
 and that's the set of generators.
 And don't worry about the notation.
 Okay, and we're still going to try and minimize the cost function here.
 Okay, now we have to decide what our decision variables are,

 but I'm actually just going to go through and start with the constraints first.
 So it's going to be subject to...
 So at each bus,
 I need power balance, right?
 So in a real power system, you need power balance at every single bus,
 which means that the power going into the bus is the same as the power going out of the bus.
 It's just Kirchhoff's laws, really.
 So we're going to have P, the generated power at a bus,
 is equal to the demand at that bus.
 It doesn't matter if some buses have no demand or no generation,
 because we're going to have lines going in there.
 So this is going to be the line power.
 I've abused notation a little bit, slightly, but this is going to be the line power.
 Now, of course, this line power, well,
 it's got a power flow equation, which we're going to have to get to,
 but before we do that, let's just do reactive power.
 The same balance is going to hold for Q.

 So that's the amount of real and reactive power we are getting from our network, right?
 Now, these have expressions.
 Pij is equal to...
 So I'm aware that if you're not doing power, these equations are going to look very foreign.
 That's the conductance.
 Vi, Vj, Bij, sine theta ij.
 These are the power flow equations.
 Sometimes you see them in a slightly different form.
 If this is confusing you from a power point of view,
 you can just work out the terms yourself, hopefully.
 Qij is equal to...
 Vi, Vj, Bij, cosine theta ij,

 so B is the susceptance,

 is going to be minus Vi, Vj,
 Gij, sine theta ij.
 Notice that due to having sines and cosines, these are non-convex.
 So the optimal power flow problem is a non-convex problem.
 That actually is a huge issue in and of itself.
 Okay, so I have now power balance and power flows.
 Don't worry if you don't understand the power flow equation, that is absolutely okay.
 We're going to have voltage limits as well, so the voltage can't be too low or too high.
 When you connect to the plug here, you expect 230 volts.
 You know it might vary up to 6% or 10% as they change in the regulations too,
 but you know you're not going to get zapped by 220 kV when you plug something in there,
 and that's very important.
 Our generators still have to be in limits.
 And this is for all generators which we're denoting by G.
 Now we have reactive power, so we need reactive power limits as well.
 Okay.
 And actually all of our lines are going to have some limit.
 That is going to be the following.
 Most of you did 280 and 380, so you know that the active power squared plus the reactive power squared
 is equal to the total apparent power through a line.
 And then if I make that into a limit, I can ensure that none of my lines are overloaded.
 I'm just going to write that down.
 No lines overloaded.
 Okay.
 So the first thing I'd like to point out here is that the problem is much, much bigger now.
 Previously my design variables were only my generated powers,
 and yes, they are still design variables,
 but actually everything here that I don't know has to be a design variable as well.
 So the things I know include, for example, the conductance, you know.

 That's fairly fixed because that is equal to the resistance of the line over this formula here.
 That's just second year electrical engineering.
 And this one is a fixed parameter, so for those not doing electrical engineering,
 these are things you can get from data sheets and so forth, so you don't need to worry too much about those.
 But nearly everything else you don't know and you have to work out.
 That includes all of my line flows, the voltage levels, the voltage angles, the reactive power flows.
 Okay.
 So for every line, I have two design variables.
 For every generator, I have two design variables.
 For every bus, I also have two design variables here.
 So when you're dealing with a huge network, suddenly this is much harder to solve than the economic dispatch problem.
 Are we kind of all right with that?
 Yes?
 Sure, so you don't need to understand what the equations are exactly.
 What I really want you to be able to notice is that it's non-convex and it's very large
 because you've got a lot of design variables and constraints for each bus and line.
 So hopefully a lot of this is quite easy to understand.
 Again, you know these are voltage limits. These are power limits.
 This is a line current limit, effectively. It just means that you're not overloading the line.
 So if you have a line from one bus to another, you need to make sure that you're not trying to send too much current or power through it.
 Otherwise, the line overheats.
 And these, of course, get substituted into here.
 It's just the power flow equations, which means that your solution has to be consistent with the physics that underpins the network.
 So this is the physical model of the network.
 It's a bit complicated without doing 382, but you don't need it for this course.

 You just need to know that your solution has to be consistent with the physics behind it.
 Does that make sense?
 So I have asked questions about that before, but then I give you the equations.
 I think already on my page there's probably some example questions.
 Maybe after the test go and have a look, and if you have problems, come and see me.
 Okay, so let's say I'm a network operator.
 How long do you think it would take me to solve this?
 This is the northeastern US system.
 Any ideas how long it would take me to solve it for this?
 Uh...
 100 hours?
 100 hours?
 Any advance on 100 hours?

 So I've given the dimensions here.
 25,000 buses, 32,000 branches.
 Remember, roughly everything times 2 is in my design variables.
 So I'm probably looking at 120,000 design variables and non-convexity.
 So 100 hours is probably a little bit too cautious,
 although it probably is about that on a personal computer,
 but they have powerful computers, so they can get it roughly around half an hour,
 which in its own way is fairly impressive.
 But it's too slow to do real-time dispatch,
 because now we need all of these to operate in about five minutes.
 So...
 Before we move on, any ideas what algorithm you would use?
 You've seen the form of the problem, you know it's non-convex,
 but it is kind of smooth.
 Most of these cost functions are probably fairly smooth as well.

 Any idea what algorithm you would use if I gave you this problem
 actually to code up and solve it?
 SQP?
 SQP is a good guess, but the problem with SQP doesn't scale very well.
 It works well for small problems,
 so if we're looking at the two bus and you say SQP, I'd be, yep, that's the one.

 Any ideas?
 Anyone?
 Um...
 Those ideas are going to be used in the solver, yes.
 But, yeah, as Lear presented it, it's more for unconstrained optimization,
 but you can use it inside the solver.
 Actually, the best algorithm is interior point.
 So interior point, because it scales well,
 naturally integrates the constraints of which we have tons,
 and it's good for non-linear, non-convex problems.
 So for this type of problem, when it gets large,
 there's absolutely no comparison to interior point.
 Things like particle swarm and genetic algorithms just struggle with the scale.
 Just think how long those chromosomes would be with all of these variables.
 It's just not a thing.
 The other reason for using interior point
 is we kind of have a reasonable idea of where things should be at.
 Like, we know that our voltage should be close to one per unit
 when we use the per unit system.
 That's just what their rated value should be.
 So, again, we know it should be about 230 volts.
 So we can usually start it fairly close to the true solution,
 and that kind of helps.
 OK, but that being said, we can't do it.
 So we usually use a simplified version,
 which is called DC optimal power flow.
 And I have to say, this is probably the worst named thing
 in electrical engineering that I'm aware of,
 because it's not about a DC network at all.
 And there is also a thing called DC optimal power flow,
 which is solving that for a DC network.
 So it is very confusing.
 I have seen a lot of confusion on this.
 But when you say DC optimal power flow,
 we're actually talking about a DC approximation
 of the AC power flow equation.
 Now, every time you simplify your problem,
 there's a trade-off.
 And in this case, it suggests that in the US,
 they could save 5% to 10% of cost,
 which is actually quite a lot.
 The reason I'm doing the US is because I have no data
 on any other countries,
 because that's the only real study I'm aware of looking at this.
 So we're solving, well, actually a surrogate problem
 that is computationally more efficient.
 So the last thing I want to do today
 is just explain the simplifications we make.
 Okay.
 Right, so the first thing with the DC power flow
 is that we ignore reactive power.
 I'm afraid that is probably fairly meaningless
 if you're not one of the people doing power.
 You might just need to stick that in your cheat sheet.
 We're going to assume all voltages are 1 per unit.
 Then we're going to assume that the angles between buses are small.
 So therefore, we have cosine of any angle
 in our formulation is going to be equal to 1,
 and sine of the angle is going to be
 approximately equal to the angle itself.
 And lastly, I think for those who've done 382
 or are doing 480, you will know that
 actually there's not much resistance on the lines.
 We don't want resistance on our lines.
 So if the resistance on the lines is smaller
 then this thing here
 is approximately zero.
 We call this a lossless network.
 Now, that's only four assumptions,
 but I'm just going to quickly go through and
 try and show you how much of a difference this makes.
 I think everyone's got the four things down there, hopefully.


 Right.
 So if I have...
 Where's my sheet?
 Here it is.
 Right.
 So if I am ignoring reactive power,
 well, I can cancel out all the reactive power flow equations.
 That's gone.
 That's gone.
 That's gone.
 That's gone.
 That's gone.
 And that's gone.
 That's not bad, huh?
 I'm going to assume all voltages are one per unit
 and all my cosines are one and all my sines are that thing itself.
 Of course, that's a lot.
 This goes to be one by one.
 All voltages being one per unit means
 I don't need to worry about voltage magnitudes.

 I can get rid of that equation.
 This thing here becomes one.
 This whole thing becomes one.
 One minus one is zero.
 One minus one is zero.
 Off it goes.
 This is one.
 That's one.
 So that's one.
 And the sine goes out here.
 Notice that those four assumptions,
 I've nearly managed to cross out the entire problem.
 So now I'm going to just go back and write what I have left.
 And this is what we actually use in the power system.
 It's what Transpower uses.

 It's what they use in Europe.
 It's what they use in the US.
 It's what they use in China.
 Everywhere we use this.
 And it's quite simple.
 So I'm just going to show you what that problem looks like.
 Now we get the generators to submit bids.

 So actually, in practice, this is going to be linear.
 Then we're going to have what we had before.
 So, so far, this is just economic dispatch.
 But I do care a little bit about my power flows.
 What did I have that wasn't crossed off?
 Well, you can go back and check your notes,
 but I'm just going to show you all there is.
 It is this.
 It's equal to beta ij.
 And, well, the power is going to have to be less than some sort of limit.
 So that's how I'm going to avoid my lines getting overloaded.
 And you know what?
 That's it.
 So it's still a much bigger problem,
 because I've got one equality constraint for every line
 and one inequality constraint for every line.
 If you remember our previous example, we had 32,000-odd lines.
 So my scale of the problem has gone up quite a lot.
 But at least I have something that's hopefully not too far away from being reasonable.
 So if I go back to this system, this is the AC optimal power flow.
 Any guesses what it would be for a DC optimal power flow?
 Notice it's a linear problem and it's quite a bit smaller.
 Although it's still not very, very small.
 The dimension of this would be about 40,000.
 Any guesses?
 90 seconds.
 90 seconds.
 Well, actually, I had written one to two minutes.
 I guess you're probably spot on.
 Yep, so it makes a difference.
 We still have to dispatch it every five minutes,
 but actually we need that contingency time,
 because what we do is we get that solution and run it through a lot of security stuff,
 which I probably will talk about tomorrow, since I'm not going to get to do it today.
 But that's how we get it to work for a big system.
 Now, students are often quite sceptical that this is actually how it works in practice,
 so I'm going to show you that.
 So if you go to the Transpower website,

 they have to specify how they schedule and dispatch each generator,
 because that affects the revenue of each generator quite a lot.
 So then you go into the model and you get this up here,
 and then you look at where the 潮流 equations are put in,

 and here you have it there.
 The 潮流, this is the P, is equal to the 导纳,

 that's the B, times the node angle voltage difference.
 So if I just switch on here, this one here,

 it's just if I'm using that equation here.
 It didn't even come up at all.
 So what we were looking at was simply this equation here,
 the node angle difference that was up on the computer screen here,
 node angle difference, that's the theta ij there.
 So really, this is how the power system runs at the moment.
 OK, so I've put a version in vector notation for those who want it here.

 That's OK.
 So the last thing I want to talk about for today,
 because I've got three minutes and I'd like to use all my time,
 what can we do to improve it?
 So one of the ideas is, you know, the voltages are not always one 标幺值,

 so let's either take real-time sensor data,
 or just run a 潮流 like you do in LFH,

 and get an idea of which buses are likely to have low voltages,

 and then I can substitute that into the formulation I had before,
 and that's going to change the term slightly,
 but that's still constant, so it doesn't ruin the linear structure of the problem.
 The biggest thing is also to have some sort of estimate of losses,
 because if you notice, my formulation here has no estimate of losses whatsoever.
 There's no 电阻 on the lines, so there are no line losses.

 So what Transpower do, and most system operators do,

 they calculate the approximate currents from the powers,
 because when you solve this, you have the powers.
 I've just realised that I should be putting my angles in here.
 So if you've got the currents, you know what the power,
 you know what the current is approximately, you can calculate that,
 and then you can guess what the I squared R is based on that.
 Now, if you have I squared R, that's going to give you,
 well, it's a nonlinear equality constraint that makes my problem non-convex,

 and more importantly for this, just nonlinear, because it's harder to solve.

 So we usually use some sort of piecewise linear approximation.
 Then the last thing we do is, once we've got this DC optimal power flow,
 we usually just run it in a standard AC power flow,
 so that's just inputting everything into a program like LFH,
 or PowerFactory, if you're used to using that,
 and seeing whether the solution is feasible,
 so whether it actually works or not.
 Why do you need a piecewise as well as a linear approximation?
 Why do you need it to be piecewise as well as a linear approximation?
 I think just because the I squared R term is kind of like this, it's more accurate to break it down into multiple linear sections.
 So at the end of the day, you're looking at a term which is like this, I squared R, right?
 And this is your loss, power loss.
 So it's just more accurate to do it like this and so forth.
 But you don't actually have to, you know.
 You could just choose a simple linear approximation.
 Okay, so we're going to get our solution and then we're just going to check that it's a feasible point.
 This is not the same as solving the original problem.
 It's just checking it's a feasible point.
 So that's quite a common thing when you do surrogate optimization.
 You get your solution, then you check it to make sure it's actually feasible.
 And if it's not feasible, we'll talk about what happens tomorrow.
 Thank you all very much.


 Well, it is actually quadratic.
 Why do you need to deal with that?
 Mainly because we want the problem to remain linear, just very fast solving.
 That is the biggest thing.
 Because there are really fast linear solvers and time is of the essence.
 If you have computational power, by all means, you could consider keeping it quadratic.
 But I think if it appears as an equality constraint, and nonlinear equality constraints ruin convexity too.

 It varies quite a lot.
 That's a very good question.
 In some scenarios, it's pretty accurate.
 In others, it's pretty inaccurate.
 That study suggested you would save 5% to 10% of costs, which actually means not very accurate, to be honest.
 In terms of research going forward, people are looking at whether you can get neural networks to predict the optimal power flow solution.
 People have tried things like particle swarm and stuff, but it's just way too slow.
 And interior point is a very mature, developed technology, so it's unlikely to get 10 times faster, which is what we need.
 Maybe you can...
 It could possibly...
 How would they have done this before computers?
 You just gave a price for your generator, pretty much.
 And then you would try and run the cheapest ones, if you could.
 Thank you.
 It might be simpler in some ways, but if you still have a cost function at each generator, you've got the same problem.
 Thank you.
 Do you remember on the positive definite side, how it's got to be stable in the square of the off-diagonals and positive eigenvalues?
 Does that make it symmetric, though?
 Yes.
 So, generally speaking, when we say positive definite, we only apply it to symmetric matrices.
 There are some people who have a wider definition of positive definite, but for most people, it just means it has to be symmetric.
 And if it's not symmetric, it's neither positive definite, semidefinite, or negative definite, or semidefinite.

 It's just not classified.
 Most of these problems, because of the structure, like if you're looking at a Hessian, the off-diagonal terms should mirror each other and make it symmetric.

 Usually that's not an issue.
 But sometimes it is, and you're right to think that, yeah.
 Thank you.
 Thank you.
 Is there any method to check if we've got multiple solutions to the problem?
 Or we can very obviously say that it's nonlinear?

 Sure.
 So if it's a convex problem, it's like a condition home.
 You don't need to do any Hessian check at all.

 Because a convex problem means that you only have one solution, so you're okay.
 But if you have multiple solutions, then yeah.