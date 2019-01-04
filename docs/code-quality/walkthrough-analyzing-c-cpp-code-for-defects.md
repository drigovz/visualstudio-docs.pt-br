---
title: 'Passo a passo: Analisando o código C/C++ em busca de defeitos'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 3a35bc07c9fe6478107162b625a824b6344898f1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53829505"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Passo a passo: Analisando o código C/C++ em busca de defeitos

Este passo a passo demonstra como analisar o código C/C++ em busca de possíveis defeitos de código usando a ferramenta de análise de código para código C/C++.

- Execute análise de código em código nativo.
- Analise os avisos de defeitos de código.
- Tratar aviso como erro.
- Anote o código-fonte para melhorar a análise de defeitos de código.

## <a name="prerequisites"></a>Pré-requisitos

- Uma cópia do [amostra de demonstração](../code-quality/demo-sample.md).
- Noções básicas sobre C/C++.

### <a name="to-run-code-defect-analysis-on-native-code"></a>Para executar a análise de defeitos de código em código nativo

1. Abra a solução de demonstração no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

     A solução de demonstração agora preenche **Gerenciador de soluções**.

2. No menu **Compilar**, clique em **Recompilar Solução**.

     A solução é compilada sem erros ou avisos.

3. Na **Gerenciador de soluções**, selecione o projeto CodeDefects.

4. No menu **Projeto**, clique em **Propriedades**.

     O **páginas de propriedade CodeDefects** caixa de diálogo é exibida.

5. Clique em **análise de código**.

6. Clique o **habilitar a análise de código para C/C++ no Build** caixa de seleção.

7. Recompile o projeto CodeDefects.

     Avisos da análise de código são exibidos na **Error List**.

### <a name="to-analyze-code-defect-warnings"></a>Para analisar os avisos de defeitos de código

1. Sobre o **modo de exibição** menu, clique em **lista de erros**.

     Dependendo do perfil do desenvolvedor que você escolheu na [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], talvez você precise apontar para **Other Windows** sobre o **exibição** menu e, em seguida, clique **lista de erros**.

2. No **Error List**, clique duas vezes o seguinte aviso:

     Aviso C6230: Conversão implícita entre tipos semanticamente diferentes: usando HRESULT em um contexto booleano.

     O editor de código exibe a linha que causou o aviso na função `bool``ProcessDomain()`. Este aviso indica que um HRESULT está sendo usado em uma instrução 'if' em que um resultado booliano é esperado.

3. Corrigi este aviso usando a macro SUCCEEDED. Seu código deve se parecer com o código a seguir:

   ```cpp
   if (SUCCEEDED (ReadUserAccount()) )
   ```

4. No **Error List**, clique duas vezes o seguinte aviso:

     Aviso C6282: Operador incorreto: atribuição a constante no contexto do teste. Foi = = pretendido?

5. Para corrigir este aviso, testando a igualdade. Seu código deve ser semelhante ao seguinte código:

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
   ```

### <a name="to-treat-warning-as-an-error"></a>Tratar aviso como erro

1. No arquivo Bug.cpp, adicione o seguinte `#pragma` instrução para o início do arquivo para tratar o aviso C6001 como um erro:

   ```cpp
   #pragma warning (error: 6001)
   ```

2. Recompile o projeto CodeDefects.

     No **lista de erros**, C6001 agora aparece como um erro.

3. Corrija os erros de C6001 dois restantes na **lista de erros** Inicializando `i` e `j` como 0.

4. Recompile o projeto CodeDefects.

     O projeto é compilado sem avisos ou erros.

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Para corrigir os avisos de anotação do código fonte no annotation.c

1. No Gerenciador de soluções, selecione o projeto de anotações.

2. No menu **Projeto**, clique em **Propriedades**.

     O **páginas de propriedades de anotações** caixa de diálogo é exibida.

3. Clique em **análise de código**.

4. Selecione o **habilitar a análise de código para C/C++ no Build** caixa de seleção.

5. Recompile o projeto de anotações.

6. No **Error List**, clique duas vezes o seguinte aviso:

     Aviso C6011: Desreferenciando ponteiro NULL 'newNode'.

     Este aviso indica falha pelo chamador para verificar o valor de retorno. Nesse caso, uma chamada para **AllocateNode** pode retornar um valor NULL (consulte o arquivo de cabeçalho para a declaração de função para AllocateNode annotations.h).

7. Abra o arquivo annotations.cpp.

8. Para corrigir este aviso, use uma instrução 'if' para testar o valor de retorno. Seu código deve se parecer com o código a seguir:

   ```cpp
   if (NULL != newNode)
   {
   newNode->data = value;
   newNode->next = 0;
   node->next = newNode;
   }
   ```

9. Recompile o projeto de anotações.

     O projeto é compilado sem avisos ou erros.

### <a name="to-use-source-code-annotation"></a>Para usar a anotação de código fonte

1. Anotar parâmetros formais e retornar o valor da função `AddTail` usando as condições anteriores e subsequentes, conforme mostrado neste exemplo:

   ```cpp
   [returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail
   (
   [SA_Pre(Null=SA_Maybe)] LinkedList* node,
   int value
   )
   ```

2. Recompile o projeto de anotações.

3. No **Error List**, clique duas vezes o seguinte aviso:

     Aviso C6011: Desreferenciando ponteiro nulo 'node'.

     Este aviso indica que o nó passado para a função pode ser nulo e indica o número de linha em que o aviso foi gerado.

4. Para corrigir este aviso, use uma instrução 'if' para testar o valor de retorno. Seu código deve se parecer com o código a seguir:

   ```cpp
   . . .
   LinkedList *newNode = NULL;
   if (NULL == node)
   {
        return NULL;
        . . .
   }
   ```

5. Recompile o projeto de anotações.

     O projeto é compilado sem avisos ou erros.

## <a name="see-also"></a>Consulte também

[Passo a passo: Analisando código gerenciado em busca de defeitos de código](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)
[análise de código para C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)