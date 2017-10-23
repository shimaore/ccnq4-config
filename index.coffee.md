    {debug} = (require 'tangible') 'ccnq4-config'

    module.exports = ->
      {CONFIG} = process.env

      debug 'CONFIG is', CONFIG
      return unless CONFIG?

`CONFIG` might be a JSON string; this is useful e.g. to pass it through a CI environment variable or other.

      if CONFIG[0] is '{'
        try
          return JSON.parse CONFIG

`CONFIG` might be the (absolute) path of the configuration file, which in turns might be JSON or any format recognized by the Node.js module loader (JavaScript, CoffeeScript, etc.) assuming the proper language is loaded at runtime.

      try
        return require CONFIG

      null
