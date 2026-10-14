# trabalho-engenharia-software-2026
Trabalho de clínica veterinária do Técnico em Informática, segundo semestre de 2026.

--(25/09/2026)--

Protótipo Figma [LINK]: https://www.figma.com/design/uxk9P2VwbDa964dw4CMAKu/Sem-t%C3%ADtulo?node-id=3-682&t=1IR1WQj4OqZvaSx7-1

## Diagramas UML

### Diagrama Casos de Uso

```mermaid
flowchart TD
    %% Atores e Entidades
    Vet([Veterinário])
    Tutor[Tutor / Dono]
    Animal[Animal / Paciente]

    %% Sistema
    subgraph Sistema ["Sistema de Clínica Veterinária"]
        UC1[Cadastrar Tutor]
        UC2[Cadastrar Animal]
        UC3[Registrar Consulta]
        UC4[Consultar Histórico Médico]
        UC5[Prescrever Tratamento]
    end

    %% Interações do Veterinário com o Sistema
    Vet --> UC1
    Vet --> UC2
    Vet --> UC3
    Vet --> UC4
    Vet --> UC5

    %% Relações das Entidades com o Sistema e entre si
    Tutor -->|possui| Animal
    UC1 -->|registra dados de| Tutor
    UC2 -->|registra dados de| Animal
    UC3 -->|atende| Animal
    Tutor -.->|acompanha| Animal
```

### Diagrama de Classe
```mermaid
classDiagram
    class Tutor {
        +String nome
        +String telefone
        +String endereco
        +String cpf
    }

    class Animal {
        +String nome
        +String especie
        +String raca
        +int idade
        +float peso
        +String historicoMedico
    }

    class Veterinario {
        +String nome
        +String crmv
        +String especialidade
        +String telefone
        +cadastrarTutor()
        +cadastrarAnimal()
        +realizarConsulta()
        +prescreverTratamento()
    }

    Tutor "1" --> "*" Animal : possui
    Veterinario "1" --> "*" Tutor : cadastra
    Veterinario "*" --> "*" Animal : atende
```
