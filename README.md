@startuml
title Diagrama de Contexto - Plataforma Educacional 

!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Container.puml

AddElementTag("v1.0", $borderColor="#d73027")
AddElementTag("v1.1", $fontColor="#d73027")
AddElementTag("backup", $fontColor="orange")

AddRelTag("backup", $textColor="orange", $lineColor="orange", $lineStyle = DashedLine())

Person(aluno, "Aluno", )
Person(professor, "Professor",)
Person(admin, "Administrator", $tags="v1.1")
Container(spa, "Plataforma educacional", )

Rel(aluno, spa, "Estuda, faz quizzes", )
Rel(professor, spa, "Cria conteúdos e avaliações",)
Rel(admin, spa, "Supervisiona usúarios e relatórios", )


@enduml

![image](https://github.com/user-attachments/assets/3ef5564a-6964-47b6-a2df-0e02e76584ae)



------------------------------------------------------------------------------------------------
-------------------------------DIAGRAMA DE CONTAINER--------------------------------------------
------------------------------------------------------------------------------------------------
@startuml
title Diagrama de Container - Plataforma Educacional 

!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Container.puml

AddElementTag("v1.0", $borderColor="#d73027")
AddElementTag("v1.1", $fontColor="#d73027")
AddElementTag("backup", $fontColor="orange")

AddRelTag("backup", $textColor="orange", $lineColor="orange", $lineStyle = DashedLine())

Person(aluno, "Aluno", )
Person(professor, "Professor",)
Person(admin, "Administrator", $tags="v1.1")

System_Boundary(plataforma, "Plataforma Educacional", ){
    Container(spa, "Frontend (Site ou app)", )
    
    Container(spaAdmin, "Backend (Servidor)",) {
        Container(autenticacao, "Autenticação", "Gerencia login e segurança")
        Container(conteudo, "Gerenciamento de Conteúdo", "Gerencia vídeos, PDFs e materiais de aula")
        Container(avaliacoes, "Avaliações e Notas", "Criação e correção de quizzes")
    }

    ContainerDb(banco, "Banco de Dados",)
}

Rel(aluno, spa, "Acessa conteúdos", )
Rel(professor, spa, "Gerencia aulas",)
Rel(admin, spa, "Supervisiona sistema", )

Rel(spa, spaAdmin, "Envia e recebe informações",)

Rel(spaAdmin, autenticacao, "Requisições de login e segurança",)
Rel(spaAdmin, conteudo, "Gerenciamento de materiais",)
Rel(spaAdmin, avaliacoes, "Envio e correção de quizzes",)

Rel(autenticacao, banco, "Dados de usuários",)
Rel(conteudo, banco, "Dados dos conteúdos",)
Rel(avaliacoes, banco, "Notas e respostas",)

@enduml
![image](https://github.com/user-attachments/assets/9468b7b9-6661-4c92-aea6-4c6a17c5d048)

