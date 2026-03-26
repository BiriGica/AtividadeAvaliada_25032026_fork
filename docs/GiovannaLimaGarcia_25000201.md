# Avaliação — Engenharia de Software
**Sistema Integrado de Gestão de Farmácia — MVP Definido pelo Estudante**

Aluno: Giovanna Lima Garcia
RA: 25000201
Data: 25/03/2026

---

# 1. Definição do MVP
- O que está **dentro** do MVP  
Meu MVP cobre o processo de gestão de estoque e produtos, compras e fornecedores. Ele foca desde a atualização no estoque depois de uma mudança, quando há necessidade de reposição em cada unidade. Ele passa pela compra destes produtos em falta vindos dos fornecedores, assim como as informação de qual produto foi comprado, qual foi a quantidade, qual o preçoo, em que dia e para qual unidade e cobre as contas a pagar para tais fornecedores.

- O que está **fora** do MVP
Ficaram fora do MVP, as operações da farmácia e atendimento ao cliente, relatórios e indicadores.

- Por que você fez essas escolhas  
Essas escolhas foram feitas, porque a gestão do estoque e como o sistema lida com isso é essencial para qeu a farmácia funcione. Este processo pode ser tratado separadamente, por causa de sua importância e prioridade para o sistema.

---

# 2. Regras de Negócio 

**RN01 —** Atualização após a compra
Quando o produto chega após a compra em ma unidade, ele deve ser atualizado no sistema automaticamente assim que reposto.

**RN02 —** Divisão por unidade
O estoque deve ser individual, separado pelas unidades da farmácia

**RN03 —** Alerta do estoque
O sistema deve avisar o usuário quando não existe estoque do produto disponível

**RN04 —** Atualização do setor financeiro depois de uma compra
O sistemadeve avisar o financeiro depois de uma compra, e este deve registrar o preço como uma conta a ser paga (ou já paga)

**RN05 —** Unidade a receber o produto
O estoque deve sempre exigir para qual unidade o produto está sendo reposto.


---

# 3. Requisitos Funcionais 

**RF01 —** Registrar os produtos com suas informações

**RF02 —** Registrar os fornecedores com todos seus dados

**RF03 —** Registrar as unidades da rede de farmácia  

**RF04 —**  Registrar a reposição após a compra com a quantidade atual do produto e o fornecedor responsável

**RF05 —** Apresentar o valor gasto com a compra de cada produto

**RF06 —** Apresentar e  registrar a unidade que está recebendo certa compra

**RF07 —** Notificar o setor financeiro da compra e valor gasto

**RF08 —** Registrar o estado atual da conta, se é a pagar ou atrasada

(Adicione mais se quiser.)

---

# 4. Requisitos Não Funcionais 
Liste os RNFs do sistema conforme seu MVP.

**RNF01 —**  O sistema deve ser feito em nuvem para todas as unidades acessaarem
**RNF02 —**  Deve poder acessar e diferenciar os perfis, porque o gerente é o único com todos os aaceos
**RNF03 —**  o tempo de atualização da compra para ser enviada ao setor finaceiro não deve demorar
**RNF04 —**  o sistema deve rodar o tempo todo


---

# 5. Casos de Uso (mínimo: 10)
### Inserir **diagrama de casos de uso geral**, demonstrando claramente:
@startuml


actor "Gerente" as gerente
actor "Setor Financeiro" as setorfinanceiro
actor "Sistema" as Sistema

package "Atividade avalaitiva - farmácia" {
  usecase "UC01 — "Cadastrar o produto" as UC01
  usecase "UC02 — "Cadastrar o Fornecedor" as UC02
  usecase "UC03 — "Cadastrar a unidade da farmácia" as UC03
  usecase "UC04 — "Registrar a compra atual" as UC04
  usecase "UC05 — "Atualizar o estoque atual" as UC05
  usecase "UC06 — "Avisar sempre quando o estoque estiver baixo" as UC06
  usecase "UC07 — Enviar o valor da compra para o setor financeiro" as UC07
  usecase "UC08 — Mostrar as contas a pagar" as UC08
  usecase "UC09 — Atualizar o estado atual das contas" as UC09
  usecase "UC10 — Autenticar o gerentwe" as UC10
}


gerente --> UC10
gerente --> UC01
gerente --> UC02
gerente --> UC03
gerente --> UC04

setorfinanceiro --> UC08
setorfinanceiro --> UC09

Sistema --> UC05
Sistema --> UC06
sistema --> UC07

UC04 ..> UC05 : <<include>>
UC04 ..> UC07 : <<include>>
UC04 ..> UC10 : <<include>>

UC01 .> UC04 : <<extend>>
UC02 .> UC04 : <<extend>>
UC06 .> UC05 : <<extend>>

@enduml

<img width="820" height="184" alt="image" src="https://github.com/user-attachments/assets/3fe4661c-bc5f-44f1-92f7-3f7d20b40030" />


---

# 6. Documentação dos Casos de Uso
Para **cada caso de uso**, utilize o template abaixo:
---

## **UC01 — Registrar o produto
**Ator(es):** Gerente
**Descrição:** gerente registra um produto novo no sistema
**Pré-condições:**  o gerente deve estar cadastrado no sistema
**Pós-condições:**  o estoque é atualizado com o produto e o setor financeiro recebe o valor da compra

### Fluxo Principal
1.  O gerente acessa a tela de cadastro de produto.
2.  O sistema pede as informações dp produto
3.  o produto é salvo no sistema

### Fluxos Alternativos / Exceções
- FA01 —  Não é possível salvar sem algum dos dados. O sistema envia um aviso 


### diagrama

<img width="343" height="312" alt="image" src="https://github.com/user-attachments/assets/1e047ae3-0025-49b4-b636-f6dc431d36f7" />

---

## **UC02 — Cadastrar o Fornecedor
**Ator(es):** Gerente
**Descrição:** gerente registra um fornecedor novo no sistema
**Pré-condições:**  o gerente deve estar cadastrado no sistema
**Pós-condições:**  o fornecedor é registrado no sistema

### Fluxo Principal
1.  O gerente acessa a tela de cadastro de fornecedor.
2.  O sistema pede as informações do fornecedor
3.  o fornecedor é salvo no sistema

### Fluxos Alternativos / Exceções
- FA01 —  Não é possível salvar sem algum dos dados. O sistema envia um aviso 


### diagrama
<img width="248" height="193" alt="image" src="https://github.com/user-attachments/assets/8b389281-4100-469a-a95f-c2ed7acef295" />
---

## **UC03 — Cadastrar a unidade da farmácia
**Ator(es):** Gerente
**Descrição:** gerente registra uma unidade fffísica no sistema
**Pré-condições:**  o gerente deve estar cadastrado no sistema, sempre
**Pós-condições:**  a unidade é registrada no sistema e pode receber compras para estoque

### Fluxo Principal
1.  O gerente acessa a tela de cadastro de unidade.
2.  O sistema pede as informações da unidade
3.  a unidade é salva no sistema

### Fluxos Alternativos / Exceções
- FA01 —  Não é possível salvar sem algum dos dados, assim como os outros cadastros. O sistema envia um aviso 


### diagrama

<img width="243" height="248" alt="image" src="https://github.com/user-attachments/assets/4df4c13d-dd5d-4fc9-aaed-2d2b46455f7a" />


---

## **UC04 — Registrar a compra atual
**Ator(es):** Gerente
**Descrição:** O gerente cadastra o produto vindo da compra ralizada com todas suas informações, como nome e fornecedor.
**Pré-condições:**  o gerente deve estar cadastrado no sistema
**Pós-condições:**  o estoque é atualizado com o produto e o setor financeiro recebe o valor da compra

### Fluxo Principal
1.  o gerente inicia a compra 
2.  o sistema verifica se o gerente está cadastrado
3.  O gerente escolhe o fornecedor de uqe comprou
4.  Ele adiciona os produtos e suas informaçoes
   

### Fluxos Alternativos / Exceções
- FA01 — Se não encontrar o fornecedor, vai para o caso de uso 2
- FA02 - Se o produto for novo, vai para o 1

### Relacionamentos
- **Extend:** UC01, UC02

@startuml
start
:Comeca registro da compra;
if (Tem o fornecedor?) then (nao)
  :Executa **UC02**;
else (sim)
endif
if (Tem o produto?) then (nao)
  :Executa **UC01**;
else (sim)
endif
:Termina de lançar a compra;
stop
@enduml

### diagrama
<img width="197" height="489" alt="image" src="https://github.com/user-attachments/assets/d2030331-b217-4107-a2e5-892e1361acd7" />

---

## **UC05 — Atualizar o estoque atual
**Ator(es):** Sistema
**Descrição:** Atualiza automaticamente o estoque da farmácia quando uma compra é feita 
**Pré-condições:**  uma compra tem que ter sido feita
**Pós-condições:**  o estoque fica com a quantidade certa de produtos

### Fluxo Principal
1.  O sistema pega os itens que foram comprados
2.  verifica qual unidade comprou 
3.  soma com o que já tem em estoque
   
@startuml
start
:Puxa os itens comprados;
:Soma as quantidades la no banco;

stop
@enduml


### diagrama

<img width="231" height="193" alt="image" src="https://github.com/user-attachments/assets/8ed84d7c-955b-495c-8258-f7cbcc937945" />

---

## **UC06 — Atualizar o estoque atual
**Ator(es):** Sistema
**Descrição:** manda uma notificação quando o estoqeu está baixo, avisando
**Pré-condições:**  o estoque de algum produto ficar muito baixo
**Pós-condições:**  o aletrta fica salvo no sistema

### Fluxo Principal
1.  o sistema percebe uqe o estoqeu do produto está baixo
2.  manda a notificação
3.  salva a notificação


@startuml
start
:Acha produto com quantidade critico;
:Manda notificacao na tela;
:Guarda no historico;
stop
@enduml

### diagrama

<img width="241" height="248" alt="image" src="https://github.com/user-attachments/assets/e96a313e-71e7-4c1e-8464-418449500fec" />

----

## **UC07 — Enviar o valor da compra para o setor financeiro
**Ator(es):** Sistema
**Descrição:** pega o valor da compra e envia para o setor financeiro
**Pré-condições:**  a compra precisa ter sido realizada
**Pós-condições:**  uma conta a pagar é feita pelo financeiro

### Fluxo Principal
1.  o sistema pega o valor da compra
2.  pega os dados do fornecedor e produto
3.  cria uma conta a pagar
4.  envia para o setor financeiro

@startuml
start
:Calcula total da conta;
:Gera a Conta a pagar;
:envia para o financeiro;
stop
@enduml


<img width="166" height="248" alt="image" src="https://github.com/user-attachments/assets/2de453ad-9455-493f-b01e-5f4789eab29d" />

---

## **UC08 — Mostrar as contas a pagar
**Ator(es):** setor financeiro
**Descrição:** o setor entra para ver os boletos e valores das compras
**Pré-condições:**  o usuario do fincanceiro tem que estar logado
**Pós-condições:**  uma lista de contas aparece

### Fluxo Principal
1.  responsável entra na parte de contas a pagar
2.  o sistema mostra o que está em aberto 
3.  mostra a lista na tela

@startuml
start
:Financeiro abre a tela;
:Sistema procura as contas;
if (Achou a conta?) then (sim)
  :Mostra a tabela na tela;
else (nao)
endif
stop
@enduml


<img width="203" height="341" alt="image" src="https://github.com/user-attachments/assets/f6601537-d08e-4f0b-b5dc-1cdc57e47905" />

---

## **UC10 — Autenticar o gerente
**Ator(es):** Gerente
**Descrição:** tela de login para verificar se é mesmo o gerente
**Pré-condições:**  o usuario tem que estar cadastrado
**Pós-condições:**  iniciar sessão

### Fluxo Principal
1.  o sistema mostra a tela de login
2.  gerente coloca a senha
3.  sistema verifica se esta no banco
4.  libera o acesso

@startuml
start
:Abre login;
:Gerente digita as info;
if (Ta certo?) then (sim)
  :Libera o acesso de boa;
else (nao)
  :Da erro de senha incoreta;
endif
stop
@enduml

<img width="355" height="312" alt="image" src="https://github.com/user-attachments/assets/534b26fb-79cc-4604-a99b-2c674262734e" />
