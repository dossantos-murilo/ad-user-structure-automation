# 🏢 Automação de Estrutura e Usuários no Active Directory

Este projeto entrega uma automação completa para ambientes **Windows Server com Active Directory**, permitindo:

1. **Criação da hierarquia de OUs (Organizational Units)** de forma padronizada via **PowerShell**, baseada em um arquivo JSON.
2. **Geração de usuários em massa**, via **Python**, respeitando a estrutura de OUs definida.
3. **Importação automática dos usuários no Active Directory**, com script em **PowerShell**, configurando atributos conforme o JSON de entrada.

---

## 🚀 Funcionalidades

- Criação de OUs de forma hierárquica e customizável.
- Geração de usuários simulados ou reais com atributos como:
  - Nome
  - Sobrenome
  - Login (samAccountName)
  - UPN
  - Senha
  - OU de destino
- Importação de usuários diretamente no AD, já vinculados às OUs criadas.
- Arquitetura flexível com base em arquivos JSON de entrada.

---

## 🛠️ Tecnologias Utilizadas

- PowerShell (>= 5.1)
- Python 3.x
- Active Directory Module for Windows PowerShell
- JSON como padrão de entrada

---

## 📂 Estrutura dos Scripts

| Script                        | Descrição                                  |
|-------------------------------|-------------------------------------------|
| `create_ou_structure.ps1`     | Cria a árvore de OUs no AD baseada no JSON |
| `generate_users.py`           | Gera os usuários com os parâmetros do JSON |
| `import_users.ps1`            | Cria os usuários no Active Directory       |

---

## ⚡ Exemplo de JSON de entrada

```json
{
  "OUs": [
    {
      "Name": "Empresa",
      "Children": [
        {
          "Name": "TI"
        },
        {
          "Name": "Financeiro"
        }
      ]
    }
  ],
  "Users": [
    {
      "FirstName": "João",
      "LastName": "Silva",
      "Login": "jsilva",
      "OU": "OU=TI,OU=Empresa,DC=exemplo,DC=com",
      "Password": "SenhaForte123!"
    }
  ]
}
