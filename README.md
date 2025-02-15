# LeadShyne (SaleOFast) Backend

# Creating New Models

## To add new Models

1. Create .js file for model in the _model_ Directory.
2. Import the model in firstConnection.js (In the last of all the model imports.)
3. Import the model in resolver.js (At the top of all the model imports.)

# Working of resolver

1. The resolver is the middleware that recives the req, res and next params.
2. Checks and validates the JWT and then handles user existence in the db.
3. It then checks if the instance of the db is present in the **connectionLock** object if it does then proceed further or else it stops the any other api to hit the main resolver ot sync data to reduce server load.
4. If there is no instance present then it creates it.
5. Then every user from the same tenent resuses the instance from **tenants** object.

# Important Notes

1. Resolver, firstConnection, middleConnection and firstConnection_small file are must.
2. Resovler is responsible for User Authentication, creating, updating and syncing model.
3. First connection is responsible for creating the model for new client.
4. The order of the model is important.
5. In the resolver all the new models should be imported at the top and also the models which needs to be synced when changed.
6. In the firstConnection all the new model must be imported at the bottom in order to maintain the reference cycle of associations.
7. All the associations must be created in the resolver.
