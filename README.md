## RUN

descomentar # command: bash -c "rails db:migrate && rails db:seed && rails s -p 3000 -b '0.0.0.0'"
e comentar  command: bash -c "rails s -p 80 -b '0.0.0.0'"
na primeira vez que rodar, dps desfazer alterações

docker-compose up frontend

## Find backend ip

docker inspect code_in_quero-backend-1

"IPAddress"
change  ./frontend/src/App.vue || linha 41