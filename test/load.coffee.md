    (require 'chai').should()
    {join} = require 'path'
    describe 'The module', ->
      it 'should load', ->
        require '..'

      it 'should parse JSON', ->
        config = require '..'
        process.env.CONFIG = '{"a":3}'
        cfg = config()
        cfg.should.have.property 'a', 3

      it 'should load file', ->
        config = require '..'
        process.env.CONFIG = join __dirname, 'test.json'
        cfg = config()
        cfg.should.have.property 'b', 5
