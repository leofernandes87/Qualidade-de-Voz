# Resultados

Este folder contém todos os resultados gerados pelo simulador, organizados em pastas de acordo com cada técnica de modulação usada nos testes.
O arquivo *script.ypnb* facilita o processo de criação dos gráficos. O ambiente *jupyter-notebook* é utilizado para permitir uma melhor visualização dos resultados.

## Requisitos do ambiente do sistema:

- Python 3
- virtualenv
- pip

## Configuração inicial 

Inicialmente deve-se clonar este repositório:

```
git clone https://github.com/leofernandes87/Qualidade-de-Voz
```
Depois de clonar o repositório deve-se acessar a pasta **Resultados**:

```
cd Qualidade-de-Voz/Resultados
```
Você pode criar um ambiente virtual:

```
python -m venv env
```
em seguida o ambiente virtual deverá ser ativado:
```
source env/bin/activate
```
caso o **pip** não esteja atualizado:
```
pip install --upgrade pip
```
e instale os requisitos do Python:
```
pip install -r requirements.txt
```
após concluir a instalação, abra o **jupyter-notebook** com:
```
jupyter-notebook
```
e execute o arquivo  **[script.ipynb](https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/Resultados/script.ipynb)**.
