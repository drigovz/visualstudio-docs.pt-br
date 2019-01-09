---
title: Crie um projeto de teste de unidade
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 8b3b3f8af1dbc2cfd745a56238694cd19cc1f16d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53824932"
---
# <a name="create-a-unit-test-project"></a>Crie um projeto de teste de unidade

Geralmente, os testes de unidade refletem a estrutura do código que está sendo testado. Por exemplo, um projeto de teste de unidade será criado para cada projeto de código do produto. O projeto de teste pode estar na mesma solução que o código de produção ou em uma solução separada. É possível ter vários projetos de teste de unidade em uma solução.

> [!NOTE]
> O local dos testes de unidade para o código nativo e a estrutura do projeto de teste podem ser diferentes da estrutura descrita neste tópico. Para obter mais informações, consulte [Escrevendo testes de unidade para C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-create-a-unit-test-project"></a>Para criar um projeto de teste de unidade:

1.  No menu **Arquivo**, escolha **Novo** e, em seguida, escolha **Projeto** (Teclado: **Ctrl**+**Shift**+**N**).

2.  Na caixa de diálogo **Novo Projeto**, expanda o nó **Instalado**, escolha a linguagem que deseja usar para o projeto de teste e clique em **Testar**.

3.  Para usar uma das estruturas de teste de unidade da Microsoft, escolha **Projeto de Teste de Unidade** na lista de modelos de projeto. Caso contrário, escolha o modelo de projeto da estrutura de teste de unidade que você deseja usar. Para testar o projeto Contas do exemplo, você nomearia o projeto como **AccountsTests**.

4.  No projeto de teste de unidade, adicione uma referência ao código que está sendo testado.  Veja como criar a referência a um projeto de código na mesma solução:

    1.  Selecione o projeto no **Gerenciador de Soluções**.

    2.  No menu **Projeto**, escolha **Adicionar Referência**.

    3.  Na caixa de diálogo **Gerenciador de Referência**, abra o nó **Solução** e escolha **Projetos**. Verifique o nome do projeto de código e feche a caixa de diálogo.

5.  Se o código que você deseja testar estiver em outro local, consulte [Gerenciando referências em um projeto](../ide/managing-references-in-a-project.md) para obter informações sobre como adicionar referências.

## <a name="next-steps"></a>Próximas etapas

 Consulte uma das seguintes seções:

**Escrevendo testes de unidade**

- [Efetuar teste de unidade em seu código](../test/unit-test-your-code.md)

- [Escrevendo Testes de Unidade para C/C++](writing-unit-tests-for-c-cpp.md)

- [Usar a estrutura do MSTest em testes de unidade](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**Executando testes de unidade**

- [Executar testes de unidade com o Gerenciador de Testes](../test/run-unit-tests-with-test-explorer.md)