docker compose down
docker compose up -d --force-recreate
docker compose ps -a
docker compose logs authelia --tail=200

docker run --rm -it authelia/authelia:latest authelia crypto hash generate argon2

docker compose restart authelia

docker exec -it authelia sh -c "sed -n '1,120p' /config/users_database.yml"

127.0.0.1 whoami.demo.local
127.0.0.1 login.demo.local
