---
title: Exemplo de demonstração | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 3a49859a8cd1c4ffb01f93bf2539fc16c42f8c4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77277890"
---
# <a name="demo-sample"></a>Amostra de demonstração
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os procedimentos a seguir mostram como criar o exemplo para [explicação: analisando o código C/C++ quanto a defeitos](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Os procedimentos criam:  
  
- Uma [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] solução chamada CppDemo.  
  
- Um projeto de biblioteca estática denominado CodeDefects.  
  
- Um projeto de biblioteca estática denominado Anotações.  
  
  Os procedimentos também fornecem o código para o cabeçalho e arquivos .cpp para as bibliotecas estáticas.  
  
### <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Criar a solução CppDemo e o projeto CodeDefects  
  
1. Clique no menu **Arquivo**, aponte para **Novo** e clique em **Novo Projeto**.  
  
2. Na lista de árvore **Tipos de projeto**, se o Visual C++ não for o idioma padrão no VS, expanda **Outros Idiomas**.  
  
3. Expanda **Visual C++** e, em seguida, clique em **Geral**.  
  
4. Em **Modelos**, clique em **Projeto Vazio**.  
  
5. Na caixa de texto **Nome**, digite **CodeDefects**.  
  
6. Marque a caixa de seleção **Criar diretório para a solução**.  
  
7. Na caixa de texto **Nome da Solução**, digite **CppDemo**.  
  
### <a name="configure-the-codedefects-project-as-a-static-library"></a>Configurar o projeto CodeDefects como uma biblioteca estática  
  
1. No Gerenciador de Soluções, clique com o botão direito do mouse em **CodeDefects** e clique em **Propriedades**.  
  
2. Expanda **Propriedades de Configuração** e, em seguida, clique em **Geral**.  
  
3. Na lista **Geral**, selecione o texto na coluna ao lado de **Extensão de Destino** e, em seguida, digite **.lib**.  
  
4. Em **Padrões do Projeto**, clique na coluna ao lado de **Tipo de Configuração** e, em seguida, clique em **Biblioteca Estática (. lib)**.  
  
### <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Adicionar o arquivo de cabeçalho e o código-fonte ao projeto CodeDefects  
  
1. No Gerenciador de Soluções, expanda **CodeDefects**, clique com o botão direito do mouse em **Arquivos de Cabeçalho**, clique em **Adicionar** e, em seguida, clique em **Novo Item**.  
  
2. Na caixa de diálogo **Adicionar Novo Item**, clique em **Código** e depois em **Arquivo de Cabeçalho (.h)**.  
  
3. Na caixa **Nome**, digite **Bug.cpp** e clique em **Adicionar**.  
  
4. Copie o código a seguir e cole-o no arquivo **bug. cpp** no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor.  
  
    ```  
    #include <windows.h>  
  
    //    
    //These 3 functions are consumed by the sample  
    //  but are not defined. This project cannot be linked!  
    //  
  
    bool CheckDomain( LPCSTR );  
    HRESULT ReadUserAccount();  
  
    //  
    //These constants define the common sizes of the   
    //  user account information throughout the program  
    //  
  
    const int USER_ACCOUNT_LEN = 256;  
    const int ACCOUNT_DOMAIN_LEN = 128;  
    ```  
  
5. No Gerenciador de Soluções, clique com o botão direito do mouse em **Arquivos de Origem**, aponte para **Novo** e clique em **Novo Item**.  
  
6. Na caixa de diálogo **Adicionar Novo Item**, clique em **Arquivo C++ (.cpp)**  
  
7. Na caixa **Nome**, digite **Bug.cpp** e clique em **Adicionar**.  
  
8. Copie o código a seguir e cole-o no arquivo Bug. h no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor.  
  
    ```  
    #include <stdlib.h>  
    #include "Bug.h"  
  
    // the user account   
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";  
    int len = 0;  
  
    bool ProcessDomain()  
    {  
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];  
        // ReadUserAccount gets a 'domain\user' input from   
        //the user into the global 'g_userAccount'  
        if (ReadUserAccount() )  
        {  
  
            // Copies part of the string prior to the '\'   
            // character onto the 'domain' buffer  
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )  
            {  
                if ( g_userAccount[len] == '\\' )   
                {  
                    // Stops copying on the domain and user separator ('\')   
                    break;  
                }  
                domain[len] = g_userAccount[len];          
            }  
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
            {  
                // '\' was not found. Invalid domain\user string.  
                delete [] domain;  
                return false;  
            }  
            else  
            {  
                domain[len]='\0';  
            }  
            // Process domain string  
            bool result = CheckDomain( domain );  
  
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
        return i+j;   
    }  
    ```  
  
9. Clique no menu **Arquivo** e em **Salvar Tudo**.  
  
### <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Adicionar o projeto Anotações e configurá-lo como uma biblioteca estática  
  
1. No Gerenciador de Soluções, clique em **CppDemo**, aponte para **Adicionar** e, em seguida, clique em **Novo Projeto**.  
  
2. Na caixa de diálogo **Adicionar Novo Projeto**, expanda Visual C++, clique em **Geral** e, em seguida, clique em **Projeto Vazio**.  
  
3. Na caixa de texto **Nome**, digite **Anotações** e clique em **Adicionar**.  
  
4. No Gerenciador de Soluções, clique com o botão direito do mouse em **Anotações** e clique em **Propriedades**.  
  
5. Expanda **Propriedades de Configuração** e, em seguida, clique em **Geral**.  
  
6. Na lista **Geral**, selecione o texto na coluna ao lado de **Extensão de Destino** e, em seguida, digite **.lib**.  
  
7. Em **Padrões do Projeto**, clique na coluna ao lado de **Tipo de Configuração** e, em seguida, clique em **Biblioteca Estática (. lib)**.  
  
### <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Adicionar o arquivo de cabeçalho e o arquivo de origem ao projeto Anotações  
  
1. No Gerenciador de Soluções, expanda **Anotações**, clique com o botão direito do mouse em **Arquivos de Cabeçalho**, clique em **Adicionar** e, em seguida, clique em **Novo Item**.  
  
2. Na caixa de diálogo **Adicionar Novo Item**, clique em **Arquivo de Cabeçalho (.h)**.  
  
3. Na caixa de texto **Nome**, digite **annotations.h** e clique em **Adicionar**.  
  
4. Copie o código a seguir e cole-o no arquivo **Annotations. h** no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor.  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
  
    struct LinkedList  
    {  
        struct LinkedList* next;  
        int data;  
    };  
  
    typedef struct LinkedList LinkedList;  
  
    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();  
  
    ```  
  
5. No Gerenciador de Soluções, clique com o botão direito do mouse em **Arquivos de Origem**, aponte para **Novo** e clique em **Novo Item**.  
  
6. Na caixa de diálogo **Adicionar Novo Item**, clique em **Código** e depois em **Arquivo C++ (.cpp)**  
  
7. Na caixa de texto **Nome**, digite **annotations.cpp** e clique em **Adicionar**.  
  
8. Copie o código a seguir e cole-o no arquivo **Annotations. cpp** no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor.  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
    #include <windows.h>  
    #include <stdlib.h>    
    #include "annotations.h"  
  
    LinkedList* AddTail( LinkedList *node, int value )  
    {  
        LinkedList *newNode = NULL;   
  
        // finds the last node  
        while ( node->next != NULL )   
        {  
            node = node->next;  
        }  
  
        // appends the new node  
        newNode = AllocateNode();   
        newNode->data = value;  
        newNode->next = 0;  
        node->next = newNode;  
  
        return newNode;  
    }  
  
    ```  
  
9. Clique no menu **Arquivo** e em **Salvar Tudo**.
