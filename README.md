# Instructions to run project:
- Network: ```docker network create goals-net```
- Database: ```docker run --name mongodb -v data:/data/db --rm -d --network goals-net -e MONGO_INITDB_ROOT_USERNAME=god -e MONGO_INITDB_ROOT_PASSWORD=jesus mongo```
- Backend: ```docker build -t goals-node . && docker run --name goals-backend -v /Users/muse/shop/Docker/Dockerize_Node_Mongodb/backend:/app -v logs:/app/logs -v /app/node_modules -e MONGODB_USERNAME=god -e MONGODB_PASSWORD=jesus --rm -d --network goals-net -p 80:80 goals-node``` (While in backend folder)
- Frontend: ```docker build -t goals-react . && docker run -v /Users/muse/shop/Docker/Dockerize_Node_Mongodb/frontend/src:/app/src --name goals-frontend --rm -d --network goals-net -p 3000:3000 goals-react``` (While in frontend folder)

Note: For the frontend script, you may come across an error where the server simply stops by itself. If that's the case, add "-it" right after 3000.