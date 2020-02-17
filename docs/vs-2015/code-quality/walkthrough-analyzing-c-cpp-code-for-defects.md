---
title: 'Walkthrough: analisando oC++ C-Code para defeitos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.assetid: eaee55b8-85fe-47c7-a489-9be0c46ae8af
caps.latest.revision: 37
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: c822dbcc6a1ece2040da22a3442dd584c3926d97
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77272442"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Instruções passo a passo: analisando código do C/C++ em busca de defeitos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tutorial demonstra como analisar C/C++ Code para possíveis defeitos de código usando a ferramenta de análise de código para CC++ /Code.  
  
 Neste tutorial, você percorre o processo de usar a análise de código para analisar o C/C++ Code para possíveis defeitos de código.  
  
 Você executará as seguintes etapas:  
  
- Execute a análise de código no código nativo.  
  
- Analise os avisos de defeito de código.  
  
- Trate o aviso como um erro.  
  
- Anote o código-fonte para melhorar a análise de defeitos de código.  
  
## <a name="prerequisites"></a>Prerequisites  
  
- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] ou [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)].  
  
- Uma cópia do [exemplo de demonstração](../code-quality/demo-sample.md).  
  
- Noções básicas sobre C/C++.  
  
### <a name="to-run-code-defect-analysis-on-native-code"></a>Para executar a análise de defeitos de código em código nativo  
  
1. Abra a solução de demonstração no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     A solução de demonstração agora preenche **Gerenciador de soluções**.  
  
2. No menu **Compilar**, clique em **Recompilar Solução**.  
  
     A solução é compilada sem erros ou avisos.  
  
3. Em **Gerenciador de soluções**, selecione o projeto CodeDefects.  
  
4. No menu **Projeto** , clique em **Propriedades**.  
  
     A caixa de diálogo **páginas de propriedades do CodeDefects** é exibida.  
  
5. Clique em **Análise de código**.  
  
6. Clique na caixa de seleção **Habilitar análise deC++ código para C/no Build** .  
  
7. Reconstrua o projeto CodeDefects.  
  
     Os avisos de análise de código são exibidos no **lista de erros**.  
  
### <a name="to-analyze-code-defect-warnings"></a>Para analisar avisos de defeito de código  
  
1. No menu **Exibir** , clique em **Lista de Erros**.  
  
     Dependendo do perfil de desenvolvedor que você escolheu no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], talvez seja necessário apontar para **outras janelas** no menu **Exibir** e, em seguida, clicar em **lista de erros**.  
  
2. No **lista de erros**, clique duas vezes no seguinte aviso:  
  
     aviso C6230: conversão implícita entre tipos semanticamente diferentes: usando HRESULT em um contexto booliano.  
  
     O editor de código exibe a linha que causou o aviso na função `bool``ProcessDomain()`. Esse aviso indica que um HRESULT está sendo usado em uma instrução ' If ' onde um resultado booliano é esperado.  
  
3. Corrija esse aviso usando a macro SUCCEEDed. Seu código deve ser semelhante ao seguinte código:  
  
    ```  
    if (SUCCEEDED (ReadUserAccount()) )  
    ```  
  
4. No **lista de erros**, clique duas vezes no seguinte aviso:  
  
     aviso C6282: operador incorreto: atribuição à constante no contexto de teste. Era = = pretendido?  
  
5. Corrija esse aviso testando a igualdade. Seu código deve ser semelhante ao seguinte código:  
  
    ```  
    if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
    ```  
  
### <a name="to-treat-warning-as-an-error"></a>Para tratar o aviso como um erro  
  
1. No arquivo Bug. cpp, adicione a seguinte instrução `#pragma` ao início do arquivo para tratar o aviso C6001 como um erro:  
  
    ```  
    #pragma warning (error: 6001)  
    ```  
  
2. Reconstrua o projeto CodeDefects.  
  
     Na **lista de erros**, C6001 agora aparece como um erro.  
  
3. Corrija os dois erros C6001 restantes na **lista de erros** inicializando `i` e `j` como 0.  
  
4. Reconstrua o projeto CodeDefects.  
  
     O projeto é compilado sem avisos ou erros.  
  
### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Para corrigir os avisos de anotação de código-fonte em Annotation. c  
  
1. Em Gerenciador de Soluções, selecione o projeto anotações.  
  
2. No menu **Projeto** , clique em **Propriedades**.  
  
     A caixa de diálogo **páginas de propriedades de anotações** é exibida.  
  
3. Clique em **Análise de código**.  
  
4. Marque a caixa de seleção **Habilitar análise deC++ código para C/no Build** .  
  
5. Recrie o projeto de anotações.  
  
6. No **lista de erros**, clique duas vezes no seguinte aviso:  
  
     Aviso C6011: desreferenciando o ponteiro nulo ' newNode '.  
  
     Esse aviso indica falha pelo chamador para verificar o valor de retorno. Nesse caso, uma chamada para **AllocateNode** pode retornar um valor nulo (consulte o arquivo de cabeçalho annotations. h para declaração de função para AllocateNode).  
  
7. Abra o arquivo annotations. cpp.  
  
8. Para corrigir esse aviso, use uma instrução ' If ' para testar o valor de retorno. Seu código deve ser semelhante ao seguinte código:  
  
     `if (NULL != newNode)`  
  
     `{`  
  
     `newNode->data = value;`  
  
     `newNode->next = 0;`  
  
     `node->next = newNode;`  
  
     `}`  
  
9. Recrie o projeto de anotações.  
  
     O projeto é compilado sem avisos ou erros.  
  
### <a name="to-use-source-code-annotation"></a>Para usar a anotação de código-fonte  
  
1. Anote os parâmetros formais e o valor de retorno da função `AddTail` usando as condições anterior e posterior, conforme mostrado neste exemplo:  
  
     `[returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail`  
  
     `(`  
  
     `[SA_Pre(Null=SA_Maybe)] LinkedList* node,`  
  
     `int value`  
  
     `)`  
  
2. Recriar projeto de anotações.  
  
3. No **lista de erros**, clique duas vezes no seguinte aviso:  
  
     Aviso C6011: desreferenciando o ponteiro nulo ' node '.  
  
     Esse aviso indica que o nó passado para a função pode ser nulo e indica o número da linha em que o aviso foi gerado.  
  
4. Para corrigir esse aviso, use uma instrução ' If ' para testar o valor de retorno. Seu código deve ser semelhante ao seguinte código:  
  
    ```  
    . . .  
    LinkedList *newNode = NULL;   
    if (NULL == node)  
    {  
         return NULL;  
        . . .  
    }  
    ```  
  
5. Recriar projeto de anotações.  
  
     O projeto é compilado sem avisos ou erros.  
  
## <a name="see-also"></a>Consulte Também  
 [Passo a passo: analisando código gerenciado em busca de defeitos de código](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)
