# Trabalho-Django-Ciclo-2
Trabalho realizado para o ciclo avaliativo da matéria de estrutura de dados, ministrada pelo professor José William.

Nome dos integrantes do projeto: Thiago Vilela Lima, Filipe Trotte, Zeneida Girão, Jarbas Cardoso, Julio Cesar, Felipe Espinola


📄 README.md: Sistema de Cadastros de Adoção de Animais 🐾
🚀 Visão Geral do Projeto
Este projeto é um sistema de gerenciamento de Cadastros de Adoção de Animais desenvolvido em Django. Ele tem como objetivo centralizar o registro de animais disponíveis para adoção, os dados dos potenciais donos e a efetivação das adoções.


⚙️ Tecnologias Utilizadas
Framework: Django (Python)

Banco de Dados: SQLite (padrão do Django)

Linguagem de Programação: Python

🧩 Estrutura de Models (Modelos de Dados)
O sistema é composto por três modelos principais que representam as entidades centrais do negócio:

Animal:

Campos: nome, idade, raça, especieAnimal.

Meta: Configurado com verbose_name e verbose_name_plural em português. A ordenação padrão é pelo id decrescente (ordering = ['-id']). OBS: Tivemos que implementar essa classe para que consertasse o problema do portal admin inserir um s ao final

Dono:

Campos: nome, email, telefone, endereco.

Adocao:

Relacionamento: Possui duas chaves estrangeiras (ForeignKey):

Animal: Referencia o animal adotado.

Dono: Referencia o novo dono.

Comportamento: Em caso de exclusão de um Animal ou Dono, o registro de Adocao correspondente também é excluído (on_delete=models.CASCADE).

Data: O campo data_Adocao registra automaticamente a data e hora da criação do registro (auto_now_add=True).

Meta: Configurado com verbose_name e verbose_name_plural em português e ordenação padrão pelo id decrescente.

🖥️ Acesso e Administração
O painel administrativo do Django foi personalizado para melhor identificação do sistema:

Título Principal (site_header): "Administração do Sistema de Cadastros"

Título da Página (site_title): "Administração de Cadastros de adoção"

Todos os modelos (Animal, Dono, Adocao) estão devidamente registrados no painel de administração (admin.py), permitindo a gestão completa dos dados via interface gráfica.

📝 Instruções de Setup e Execução
Para configurar e rodar o projeto localmente:

Pré-requisitos: Certifique-se de ter o Python e o pip instalados.

Instalar Django:

Bash

pip install django
Configurar a Aplicação: O aplicativo principal de modelos é chamado Cadastros e já está listado em INSTALLED_APPS.

Executar Migrações: Crie o banco de dados inicial com base nos modelos definidos:

Bash

python manage.py makemigrations Cadastros
python manage.py migrate
Criar Superusuário (Admin): Necessário para acessar o painel administrativo:

Bash

python manage.py createsuperuser
Rodar o Servidor: Inicie o servidor de desenvolvimento: Bash ou use o terminal do VsCode

python manage.py runserver
Acessar:

Site: Acesse http://127.0.0.1:8000/

Administração: Acesse http://127.0.0.1:8000/admin/ (use as credenciais do superusuário).

📌 Alterações e Implementações do Grupo
Com base nos arquivos fornecidos, as principais alterações e implementações realizadas pela equipe no projeto foram:

1. Modelos de Dados (models.py)
Criação dos Modelos: Implementação dos modelos de dados Animal, Dono e Adocao.

Relacionamento Adocao: Configuração do relacionamento muitos-para-um (ForeignKey) entre Adocao e as entidades Animal e Dono.

Regra de Exclusão: Definição da regra on_delete=models.CASCADE nas chaves estrangeiras, garantindo a integridade referencial.

Timestamp: Uso de data_Adocao = models.DateField(auto_now_add=True) para registrar automaticamente a data da adoção.

Metadados (Meta): Adição da classe Meta nos modelos Animal e Adocao para:

Definir nomes em português (verbose_name, verbose_name_plural).

Configurar a ordenação padrão (ordering = ['-id']).

2. Painel Administrativo (admin.py)
Personalização: Alteração dos títulos do painel de administração com admin.site.site_header e admin.site.site_title.

Registro de Modelos: Registro de todos os três modelos (Animal, Dono, Adocao) para que sejam gerenciáveis via interface.

3. Configurações Globais (settings.py e apps.py)
Configuração Regional: Definição de LANGUAGE_CODE = 'pt-br' e TIME_ZONE = 'America/Sao_Paulo' para adequação ao contexto brasileiro.

Registro de App: Inclusão da aplicação Cadastros na lista INSTALLED_APPS.

Essas implementações estabelecem a estrutura fundamental do banco de dados e a interface administrativa do Sistema de Cadastros de Adoção.
