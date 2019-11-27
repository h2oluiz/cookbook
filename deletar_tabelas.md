### Postgres: Deletando todas as tabelas de sua base de dados sem precisar da drop

Muitas vezes queremos fazer o backup->restore de uma base de dados ai acabava tendo de apagar a base de dados re-criar ela e depois fazer o restore.
Olha i o caminha mais fácil para essa tarefa:

    drop schema public cascade;
    create schema public;

fonte: http://redrails.com.br/desenvolvimento/dicas/2014/12/16/postgres-deletando-todas-as-tabelas-de-sua-base-de-dados-sem-precisar-da-drop.html

