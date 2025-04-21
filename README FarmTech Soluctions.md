# FIAP - Faculdade de Informática e Administração Paulista


<p align="center">
<a href= "https://www.fiap.com.br/"><img src="assets/logo-fiap.png" alt="FIAP - Faculdade de Informática e Admnistração Paulista" border="0" width=40% height=40%></a>
</p>

<br>

# Projeto: Um Mapa do Tesouro

## Top Three FIAP

### Integrantes:
- Caio Oliveira: https://www.linkedin.com/in/caiooliveiraeti/ 
- Enéas Moreira: https://www.linkedin.com/in/en%C3%A9as-moreira-4bbaab136/
- William Xavier: https://www.linkedin.com/in/williamxavier22/  

## 👩‍🏫 Professores:
### Tutor(a) 
- <a href="https://www.linkedin.com/in/lucas-gomes-moreira-15a8452a/">Nome do Tutor</a>

### Coordenador(a)
- <a href="https://www.linkedin.com/in/andregodoichiovato/">Nome do Coordenador</a>

### O Projeto

O projeto visa desenvolver um sistema de armazenamento e análise de dados provenientes de sensores utilizados por um produtor rural para ajustar a irrigação e aplicação de nutrientes na plantação. Os sensores monitoram:

- **S1:** Sensor de Umidade
- **S2:** Sensor de pH
- **S3:** Sensor de Nutrientes (Fósforo e Potássio)

Com base nos dados, o sistema sugerirá ajustes e otimizações, podendo prever necessidades futuras tanto de insumos quanto de irrigação, visando otimizar os resultados da cultura.

## Objetivo e Abordagem

Definir os fatores que influenciam:
- Umidade do solo
- Acidez (pH)
- Concentração de NPK

O foco será nos fatores que podem ser medidos com sensores.

### Fatores por Indicador

#### Umidade
- Precipitação
- Tipo de solo
- Vegetação
- Temperatura

#### Acidez (pH)
- Matéria orgânica
- Atividade microbiana
- Adubação corretiva
- Lixiviação

#### Concentração de NPK
- Textura do solo
- Ciclagem de nutrientes
- pH do solo
- Práticas agrícolas

## Tipos de Sensores

### Sensor de Umidade (Capacitivo)
- Medição: % VWC (Volumetric Water Content)
- Faixas típicas:
  - Solo seco: 5–15%
  - Ideal: 20–40%
  - Saturado: 50%+
- Exemplo: Milho (25–35%), Alface (30–40%), Café (20–35%)

### Sensor de pH

- Mede íons H⁺ (0–14)
- Faixa ideal: 5,5 a 7,0
- Ajustes:
  - Solo ácido (pH < 5,5): calcário
  - Solo alcalino (pH > 7,5): enxofre ou matéria orgânica

### Sensor de NPK

- Medição via espectrofotometria ou condutividade
- Unidades: mg/kg ou ppm

| Nutriente | Unidade |
| --------- | ------- |
| Nitrogênio (N) | mg/kg ou ppm |
| Fósforo (P) | mg/kg ou ppm |
| Potássio (K) | mg/kg ou ppm |


## Entidades do Sistema

### AREA

| Atributo        | Descrição                         | Tipo de Dado | Chave       |
|-----------------|-----------------------------------|--------------|-------------|
| cod_area        | Identificador da área             | Numérico     | Primária    |
| area_cult_ha    | Área cultivável                   | Numérico     | -           |
| umidade_inicial | Umidade inicial do solo           | Numérico     | -           |
| acidez_inicial  | pH inicial                        | Numérico     | -           |
| n_inicial       | Nitrogênio inicial                | Numérico     | -           |
| p_inicial       | Fósforo inicial                   | Numérico     | -           |
| k_inicial       | Potássio inicial                  | Numérico     | -           |
| nome_area       | Nome identificador                | Varchar      | -           |

### SAFRA_IMPLANTACAO

| Atributo           | Descrição                              | Tipo de Dado | Chave       |
|--------------------|----------------------------------------|--------------|-------------|
| id_safra           | Identificador da safra                 | Numérico     | Primária    |
| cod_area           | Relação com AREA                       | Numérico     | Estrangeira |
| cod_cultura1       | Relação com CULTURA                    | Numérico     | Estrangeira |
| id_leitura_npk     | Sensor NPK                             | Numérico     | Estrangeira |
| id_leitura_ph      | Sensor pH                              | Numérico     | Estrangeira |
| id_leitura_umidade | Sensor Umidade                         | Numérico     | Estrangeira |
| data_plantio       | Data de plantio                        | Numérico     | -           |
| data_colheita      | Data de colheita                       | Numérico     | -           |
| produção_total     | Produção total                         | Numérico     | -           |

### CULTURA

| Atributo        | Descrição                  | Tipo de Dado | Chave    |
|-----------------|----------------------------|--------------|----------|
| cod_cultura     | Identificador da cultura   | Numérico     | Primária |
| tipo_cultura    | Nome da cultura            | Varchar      | -        |
| acidez_ideal    | Acidez ideal               | Numérico     | -        |
| umidade_ideal   | Umidade ideal              | Numérico     | -        |
| p_ideal         | Fósforo ideal              | Numérico     | -        |
| n_ideal         | Nitrogênio ideal           | Numérico     | -        |
| k_ideal         | Potássio ideal             | Numérico     | -        |
| produção_ideal  | Produção esperada (t/ha)   | Numérico     | -        |

### SENSOR_NPK

| Atributo            | Descrição                 | Tipo de Dado | Chave    |
|---------------------|---------------------------|--------------|----------|
| id_leitura_npk      | ID da leitura             | Numérico     | Primária |
| leitura_fosforo     | Valor do fósforo (P)      | Numérico     | -        |
| leitura_potassio    | Valor do potássio (K)     | Numérico     | -        |
| leitura_nitrogenio  | Valor do nitrogênio (N)   | Numérico     | -        |
| data_leitura_npk    | Data da leitura           | Numérico     | -        |
| hora_leitura_npk    | Hora da leitura           | Numérico     | -        |

### SENSOR_UMIDADE

| Atributo              | Descrição             | Tipo de Dado | Chave    |
|-----------------------|-----------------------|--------------|----------|
| id_leitura_umidade    | ID da leitura         | Numérico     | Primária |
| leitura_umidade       | Valor da umidade      | Numérico     | -        |
| data_leitura_umidade  | Data da leitura       | Numérico     | -        |
| hora_leitura_umidade  | Hora da leitura       | Numérico     | -        |

### SENSOR_ACIDEZ

| Atributo              | Descrição             | Tipo de Dado | Chave    |
|-----------------------|-----------------------|--------------|----------|
| id_leitura_acidez     | ID da leitura         | Numérico     | Primária |
| leitura_acidez        | Valor do pH           | Numérico     | -        |
| data_leitura_acidez   | Data da leitura       | Numérico     | -        |
| hora_leitura_acidez   | Hora da leitura       | Numérico     | -        |

## Modelo Relacional

- **AREA** → 1:N → **SAFRA_IMPLANTACAO**
- **CULTURA** → 1:N → **SAFRA_IMPLANTACAO**
- **SAFRA_IMPLANTACAO** → N:1 → **SENSOR_UMIDADE**, **SENSOR_ACIDEZ**, **SENSOR_NPK**


## 📁 Estrutura de pastas

Dentre os arquivos e pastas presentes na raiz do projeto, definem-se:

- <b>.github</b>: Nesta pasta ficarão os arquivos de configuração específicos do GitHub que ajudam a gerenciar e automatizar processos no repositório.

- <b>assets</b>: aqui estão os arquivos relacionados a elementos não-estruturados deste repositório, como imagens.

- <b>config</b>: Posicione aqui arquivos de configuração que são usados para definir parâmetros e ajustes do projeto.

- <b>document</b>: aqui estão todos os documentos do projeto que as atividades poderão pedir. Na subpasta "other", adicione documentos complementares e menos importantes.

- <b>scripts</b>: Posicione aqui scripts auxiliares para tarefas específicas do seu projeto. Exemplo: deploy, migrações de banco de dados, backups.

- <b>src</b>: Todo o código fonte criado para o desenvolvimento do projeto ao longo das 7 fases.

- <b>README.md</b>: arquivo que serve como guia e explicação geral sobre o projeto (o mesmo que você está lendo agora).
