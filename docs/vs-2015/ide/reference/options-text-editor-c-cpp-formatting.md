---
title: Opções, Editor de Texto, C-C++, Formatação | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- C++
helpviewer_keywords:
- Text Editor Options dialog box, formatting
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5ad06dfb32c301985eb4976f6c89c7be1e0e68da
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662338"
---
# <a name="options-text-editor-cc-formatting"></a>Opções, Editor de Texto, C/C++, Formatação
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Permite alterar o comportamento padrão do Editor de Códigos quando você está programando no C ou C++.

 Para acessar essa página, na caixa de diálogo **Opções**, no painel esquerdo, expanda **Editor de Texto**, expanda **C/C++** e clique em **Formatação**.

> [!NOTE]
> Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="cc-options"></a>Opções do C/C++
 **Habilitar dicas de ferramentas de informações rápidas automáticas** Habilita ou desabilita o recurso IntelliSense de informações rápidas.

## <a name="inactive-code"></a>Código inativo
 **Mostrar blocos de código inativos** O código que está inativo devido a `#ifdef` declarações é colorido de forma diferente para ajudá-lo a identificá-lo.

 **Desabilitar a opacidade de código inativo** O código inativo pode ser identificado usando cores em vez de transparência.

 **Porcentagem de opacidade de código inativo** O grau de opacidade para blocos de código inativos pode ser personalizado.

## <a name="indentation"></a>Recuo
 **Recuar chaves** Você pode configurar como as chaves são alinhadas quando você pressiona ENTER depois de iniciar um bloco de código, por exemplo, uma função ou um loop de `for`. As chaves podem ser alinhadas com o primeiro caractere do bloco de códigos ou recuadas.

 **Recuo automático na guia** Você pode configurar o que acontece na linha de código atual quando você pressiona TAB. A linha é recuada ou uma tabulação é inserida.

## <a name="miscellaneous"></a>Diversos
 **Enumerar os comentários na janela de lista de tarefas** O editor pode verificar os arquivos de código-fonte aberto em busca de palavras predefinidas nos comentários. Ele cria uma entrada na janela **Lista de Tarefas** para qualquer palavra-chave encontrada.

 **Realçar tokens correspondentes** Quando o cursor está ao lado de uma chave, o editor pode realçar a chave correspondente para que você possa ver mais facilmente o código contido.

## <a name="outlining"></a>Estrutura de tópicos
 **Entrar no modo de estrutura de tópicos quando os arquivos forem abertos** Quando você coloca um arquivo no editor de texto, pode habilitar o recurso de estrutura de tópicos. Para obter mais informações, consulte [Estrutura de tópicos](../../ide/outlining.md). Quando essa opção é selecionada, o recurso de estrutura de tópicos é habilitado quando você abre um arquivo.

 **Estrutura de tópicos automática de blocos de região de #pragma** Quando essa opção é selecionada, a estrutura de tópicos automática para [diretivas pragma](https://msdn.microsoft.com/library/9867b438-ac64-4e10-973f-c3955209873f) é habilitada. Isso permite expandir ou recolher blocos de região pragma no modo de estrutura de tópicos.

 **Estrutura de tópicos automática de blocos de instrução** Quando essa opção é selecionada, a estrutura de tópicos automática é habilitada para as seguintes construções de instrução:

- [if-else](https://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2)

- [Instrução switch (C++)](https://msdn.microsoft.com/library/6c3f3ed3-5593-463c-8f4b-b33742b455c6)

- [Instrução while (C++)](https://msdn.microsoft.com/library/358dbe76-5e5e-4af5-b575-c2293c636899)

## <a name="see-also"></a>Veja também
 [Caixa de diálogo geral, ambiente, opções](../../ide/reference/general-environment-options-dialog-box.md) [usando o IntelliSense](../../ide/using-intellisense.md)
