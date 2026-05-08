# Projeto BD - Agregação e Auto-relacionamento
Este projeto apresenta a modelagem de um banco de dados utilizando Diagramas ER no formato Mermaid. O objetivo da atividade é representar relacionamentos entre entidades, incluindo conceitos importantes de modelagem como autorelacionamento, dependência de existência e agregação.
O diagrama foi desenvolvido utilizando a sintaxe erDiagram do Mermaid, permitindo a visualização estrutural das entidades e seus relacionamentos de forma simples e organizada.






# Uso do Autorelacionamento
O autorelacionamento ocorre na tabela FUNCIONARIO, pois um funcionário pode supervisionar outros funcionários. Para isso, o campo supervisor_id referencia o próprio id da tabela.

A dependência de existência aparece em DEPENDENTE, já que um dependente precisa estar vinculado a um funcionário para existir no sistema.

A relação entre funcionário e projeto foi separada na tabela ALOCACAO, pois um funcionário pode participar de vários projetos e um projeto pode ter vários funcionários.

# Uso da Agregação
A agregação foi representada por ALOCACAO_EQUIPAMENTO. Essa tabela registra o uso de equipamentos dentro de uma alocação específica.
Assim, o equipamento fica independente, sem depender diretamente de funcionário ou projeto, permitindo que a mesma máquina seja usada
por diferentes funcionários em diferentes projetos.


# Diagrama Mermaid

```mermaid
erDiagram
    FUNCIONARIO ||--o{ FUNCIONARIO : supervisiona
    FUNCIONARIO ||--o{ DEPENDENTE : possui
    FUNCIONARIO ||--o{ ALOCACAO : realiza
    PROJETO ||--o{ ALOCACAO : recebe
    ALOCACAO ||--o{ ALOCACAO_EQUIPAMENTO : utiliza
    EQUIPAMENTO ||--o{ ALOCACAO_EQUIPAMENTO : eh_usado

    FUNCIONARIO {
        int id PK
        string nome
        int supervisor_id FK
    }

    DEPENDENTE {
        int id PK
        string nome
        int funcionario_id FK
    }

    PROJETO {
        int id PK
        string nome
    }

    ALOCACAO {
        int id PK
        int funcionario_id FK
        int projeto_id FK
        date data_inicio
        date data_fim
    }

    EQUIPAMENTO {
        int id PK
        string nome
        string numero_patrimonio
    }

    ALOCACAO_EQUIPAMENTO {
        int id PK
        int alocacao_id FK
        int equipamento_id FK
        date data_uso
        string observacao
    }
























 
