---
title: Projeto de C++ de exemplo para análise de código
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 84f6ddc2012617a5216c58fa0761dc100fb8942f
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75402752"
---
# <a name="sample-c-project-for-code-analysis"></a>Projeto de C++ de exemplo para análise de código

Os procedimentos a seguir mostram como criar o exemplo para o [passo a passo: analisarC++ C/Code quanto a defeitos](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Os procedimentos criam:

- Um [! INCLUDEvsprvs] solução denominada CppDemo.

- Um projeto de biblioteca estática denominado CodeDefects.

- Um projeto de biblioteca estática denominado Anotações.

Os procedimentos também fornecem o código para o cabeçalho e arquivos *.cpp* para as bibliotecas estáticas.

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Criar a solução CppDemo e o projeto CodeDefects

1. Abra o [! INCLUDEvsprvs] e selecione **criar um novo projeto**

2. Alterar filtro de idioma para**C++**

3. Selecione **projeto vazio** e clique em **Avançar**

4. Na caixa de texto **nome do projeto** , digite **CodeDefects**

5. Na caixa de texto **nome da solução** , digite **CppDemo**

6. Clique em **Criar**

## <a name="configure-the-codedefects-project-as-a-static-library"></a>Configurar o projeto CodeDefects como uma biblioteca estática

1. No Gerenciador de Soluções, clique com o botão direito do mouse em **CodeDefects** e clique em **Propriedades**.

2. Expanda **Propriedades de Configuração** e, em seguida, clique em **Geral**.

3. Na lista **geral** , altere **tipo de configuração**para **biblioteca estática (. lib)** .

4. Na lista **avançado** , altere a **extensão do arquivo de destino** para **. lib**

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Adicionar o arquivo de cabeçalho e o código-fonte ao projeto CodeDefects

1. No Gerenciador de Soluções, expanda **CodeDefects**, clique com o botão direito do mouse em **Arquivos de Cabeçalho**, clique em **Adicionar** e, em seguida, clique em **Novo Item**.

2. Na caixa de diálogo **Adicionar Novo Item**, clique em **Código** e depois em **Arquivo de Cabeçalho (.h)** .

3. Na caixa **Nome**, digite **Bug.h** e clique em **Adicionar**.

4. Copie o código a seguir e cole-o no arquivo *bug. h* no editor.

```cpp
#pragma once

#include <windows.h>

// These functions are consumed by the sample
// but are not defined. This project cannot be linked!
bool CheckDomain(LPCTSTR);
HRESULT ReadUserAccount();

// These constants define the common sizes of the
// user account information throughout the program
const int USER_ACCOUNT_LEN = 256;
const int ACCOUNT_DOMAIN_LEN = 128;
```

5. No Gerenciador de Soluções, clique com o botão direito do mouse em **Arquivos de Origem**, aponte para **Novo** e clique em **Novo Item**.

6. Na caixa de diálogo **Adicionar Novo Item**, clique em **Arquivo C++ (.cpp)**

7. Na caixa **Nome**, digite **Bug.cpp** e clique em **Adicionar**.

8. Copie o código a seguir e cole-o no arquivo *bug. cpp* no editor.

```cpp
#include "Bug.h"

// the user account
TCHAR g_userAccount[USER_ACCOUNT_LEN] = {};
int len = 0;

bool ProcessDomain()
{
    TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];
    // ReadUserAccount gets a 'domain\user' input from
    //the user into the global 'g_userAccount'
    if (ReadUserAccount())
    {
        // Copies part of the string prior to the '\'
        // character onto the 'domain' buffer
        for (len = 0; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != L'\0'); len++)
        {
            if (g_userAccount[len] == '\\')
            {
                // Stops copying on the domain and user separator ('\')
                break;
            }
            domain[len] = g_userAccount[len];
        }
        if ((len = ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
        {
            // '\' was not found. Invalid domain\user string.
            delete[] domain;
            return false;
        }
        else
        {
            domain[len] = '\0';
        }
        // Process domain string
        bool result = CheckDomain(domain);

        delete[] domain;
        return result;
    }
    return false;
}

int path_dependent(int n)
{
    int i;
    int j;
    if (n == 0)
        i = 1;
    else
        j = 1;
    return i + j;
}
```

9. Clique no menu **Arquivo** e em **Salvar Tudo**.

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Adicionar o projeto Anotações e configurá-lo como uma biblioteca estática

1. No Gerenciador de Soluções, clique em **CppDemo**, aponte para **Adicionar** e, em seguida, clique em **Novo Projeto**.

2. Na caixa de diálogo **Adicionar um novo projeto** , altere filtro de idioma **C++** para e selecione **projeto vazio** e clique em **Avançar**.

3. Na caixa de texto **nome do projeto** , digite **anotações**e clique em **criar**.

4. No Gerenciador de Soluções, clique com o botão direito do mouse em **Anotações** e clique em **Propriedades**.

5. Expanda **Propriedades de Configuração** e, em seguida, clique em **Geral**.

6. Na lista **geral** , altere **tipo de configuração**para e clique em **biblioteca estática (. lib)** .

7. Na lista **avançado** , selecione o texto na coluna ao lado de **extensão de arquivo de destino**e digite **. lib**.


## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Adicionar o arquivo de cabeçalho e o arquivo de origem ao projeto Anotações

1. No Gerenciador de Soluções, expanda **Anotações**, clique com o botão direito do mouse em **Arquivos de Cabeçalho**, clique em **Adicionar** e, em seguida, clique em **Novo Item**.

2. Na caixa de diálogo **Adicionar Novo Item**, clique em **Arquivo de Cabeçalho (.h)** .

3. Na caixa de texto **Nome**, digite **annotations.h** e clique em **Adicionar**.

4. Copie o código a seguir e cole-o no arquivo *Annotations. h* no editor.

```cpp
#pragma once
#include <sal.h>

struct LinkedList
{
    struct LinkedList* next;
    int data;
};

typedef struct LinkedList LinkedList;

_Ret_maybenull_ LinkedList* AllocateNode();
```

5. No Gerenciador de Soluções, clique com o botão direito do mouse em **Arquivos de Origem**, aponte para **Novo** e clique em **Novo Item**.

6. Na caixa de diálogo **Adicionar Novo Item**, clique em **Código** e depois em **Arquivo C++ (.cpp)**

7. Na caixa de texto **Nome**, digite **annotations.cpp** e clique em **Adicionar**.

8. Copie o código a seguir e cole-o no arquivo *Annotations. cpp* no editor.

```cpp
#include "annotations.h"

LinkedList* AddTail(LinkedList* node, int value)
{
    // finds the last node
    while (node->next != nullptr)
    {
        node = node->next;
    }

    // appends the new node
    LinkedList* newNode = AllocateNode();
    newNode->data = value;
    newNode->next = 0;
    node->next = newNode;

    return newNode;
}
```

9. Clique no menu **Arquivo** e em **Salvar Tudo**.


A solução agora está completa e deve ser compilada sem erros.
