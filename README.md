# SqlCommands

## LISTAGG
select 
    count(pessoa.id_pessoa)
    ,LISTAGG(pessoa.id_pessoa, '; ' ON OVERFLOW TRUNCATE)
         WITHIN GROUP (ORDER BY pessoa.id_pessoa) "id_list"
    ,min(pessoa.nome)
    ,min(pessoa.cpf)
    ,max(pessoa.data_inclusao)
from pessoa
group by 
    pessoa.cpf
having
    count(pessoa.id_pessoa) > 1 and count(pessoa.id_pessoa) < 3
    ;
