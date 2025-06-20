// middleware to validate request body against schema

      const validateBody = (schema) => {
        return (req, res, next) => {
          const { error } = schema.validate(req.body);

          if (error) {
            return res.status(400).json({ error: error.details[0].message });
          }

          next();
        };
      };


In this example, the middleware function takes a schema as an argument and returns a function that can be used as middleware in your application.

The schema argument is an instance of a Joi schema, which is a popular Node.js package for data validation. You can define the schema for your document using the Joi.object() method and its various validation methods to specify the expected shape of the data.

The middleware function then returns a function that takes the standard req, res, and next parameters. The validate() method of the Joi schema is used to validate the req.body against the schema. If there is an error, the middleware function will return a 400 Bad Request status code and the error message from Joi. If there is no error, the middleware function will call next() to pass control to the next middleware or route handler.

To use this middleware function in your application, you can simply call it before your route handler that creates the document, like this:

      // example route handler to create a document
      app.post('/api/documents', validateBody(mySchema), async (req, res) => {
        // create document and save to database
        // return success response
      });
      
In Express, middleware functions have access to the req, res, and next objects by default. When you define a middleware function using app.use() or app.METHOD(), Express passes these objects to the middleware function as arguments.

In the case of the validateBody() middleware function, it returns a function that takes the standard req, res, and next parameters. When this returned function is called by Express, it will be passed the req, res, and next objects as arguments.
