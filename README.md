Industry
========

Factories for backbone. 

Comming soon to a rainforest near you :)

    r.factories.step = ModelFactory.define (f) ->
      f.base -> 
        id: -> "step_#{f.sequence('id')}"
        created_at: -> new Date().toString()
    
      f.trait 'passed' , -> 
        result: 'passed'
    
      f.trait 'failed' , -> 
        result: 'failed'
    
    sharedTraits = {
      passed: ->
        result: 'passed'
      failed: ->
        result: 'failed'
    }
    
    
    r.factories.passedStep = ModelFactory.define parent: r.factories.step, traits: sharedTraits, (f) ->
      f.base ->
        result: 'passed'
        
    r.factories.test = ModelFactory.define (f) ->
      f.base -> 
        id: 'test_id'
        steps: ->
          r.factories.step.attributesFor() for i in 5
      
    
    
    test = new Test
    r.factories.step.create('passed', test_id: test.id)
    r.factories.step.attributesFor('passed', 'failed')
    
    
    CollectionFactory.create(r.factories.step, 5)
    
    r.factories.step = ModelFactory.define ->
      @base ->
        "id": -> @sequence('id')
        "created_at":"2013-02-28T17:30:20Z"
        "test_id": -> @sequence('test_id')
        "action":"My action"
        "response":"My Response"
        "ord": -> @sequence('ord')
        "pretest_step": true
    
    func()
    
