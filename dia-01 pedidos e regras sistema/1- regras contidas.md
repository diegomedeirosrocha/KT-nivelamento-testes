# regras de negocio

## tirar carta

Como product owner desejo criar um sistema para validar se usuário pode tirar carteira de motorista com base no UF / estado.

### Regras

1. v1 regras conhecidas
Caso cliente tenha menos que 18 anos `nao pode tirar carta`, caso contratio cliente `pode tirar carta`

| regra   | resultado            |
| ------- | -------------------- |
| 18 anos | pode tirar carta     |
| 19 anos | pode tirar carta     |
| 70 anos | pode tirar carta     |
| 17 anos | nao pode tirar carta |

cola.. -> cola formatar tabela (Ctrl+Shift+I)

2. regras api
Caso cliente tenha menos que 15 anos `nao pode tirar carta`, caso ele tenha maior que 18 anos o cliente `pode tirar carta`, caso esteja nesse intervalo ele `necessita de autorizacao dos pais`. Se cliente for do estado/UF de `RR` ele so pode tirar carta se tiver mais de 19 anos.

- UF `SP`
| regra                | uf  | resultado                         |
| -------------------- | --- | --------------------------------- |
| < 15 anos            | SP  | nao pode tirar carta              |
| >= 15 anos a 18 anos | SP  | necessita de autorizacao dos pais |
| > 18 anos            | SP  | pode tirar carta                  |

- UF `RR`
| regra     | uf  | resultado                         |
| --------- | --- | --------------------------------- |
| = 18 anos | RR  | necessita de autorizacao dos pais |

- campos envio:
- texto name;
- texto secondName;
- inteiro age;
- texto uf;

- campos retorno:
- texto name;
- texto secondName;
- inteiro age;
- texto uf;
- inteiro id;
- inteiro status;
