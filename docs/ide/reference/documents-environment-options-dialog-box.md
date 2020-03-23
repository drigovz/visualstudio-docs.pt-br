---
title: Caixa de diálogo Documentos, Ambiente, Opções
ms.date: 03/28/2019
ms.topic: reference
f1_keywords:
- VS.Environment.Documents
- VS.ToolsOptionsPages.Environment.Documents
helpviewer_keywords:
- Documents Environment Options dialog box
- defaults, directories
- error messages, customizing
- files [Visual Studio], default options
- files [Visual Basic], auto-loading modified
- windows, customizing environment
- in-memory editing
- folders [Visual Studio], specifying where Open File goes
- Open File dialog box
- windows, enabling re-use of current
- notifications, files changed
- files [Visual Studio], displaying in Solution Explorer
- default directories
- read-only files, editing
- Options dialog box, showing Miscellaneous Files
- directories [Visual Studio], IDE environment options
- Options dialog box, Documents page
- warnings, files changed
- Solution Explorer, displaying files in
ms.assetid: 4e3ccf1b-cd68-4db6-9470-710c911b47fc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7813a2e7686bef5a146e7472bce7f2c24baf9cd2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570057"
---
# <a name="options-dialog-box-environment--documents"></a>Caixa de diálogo \> opções: Documentos do ambiente

Use esta página da caixa de diálogo **Opções** para controlar a exibição de documentos no IDE (ambiente de desenvolvimento integrado) e gerenciar alterações externas em documentos e arquivos. Para acessar essa caixa de diálogo, clique em **Opções**, no menu **Ferramentas** e selecione **Ambiente** > **Documentos**.

**Detectar quando o arquivo foi alterado fora do ambiente**

Quando essa opção é selecionada, uma mensagem notifica você imediatamente sobre alterações em um arquivo aberto que foram feitas por um editor fora do IDE. A mensagem permite recarregar o arquivo do armazenamento.

**Recarregar arquivos modificados a menos que haja alterações não salvas**

Quando **Detectar quando o arquivo foi alterado fora do ambiente** está selecionado e um arquivo aberto no IDE é alterado fora do IDE, uma mensagem de aviso é gerada por padrão. Se essa opção estiver habilitada, nenhum aviso será exibido e o documento será recarregado no IDE para acompanhar alterações externas.

**Permitir a edição de arquivos somente leitura; avisar ao tentar salvar**

Quando essa opção está habilitada, você pode abrir e editar um arquivo somente leitura. Ao terminar, você deverá usar o comando **Salvar Como** para salvar o arquivo com um novo nome, se desejar salvar um registro de suas alterações.

**Abrir arquivo usando o diretório do documento ativo no momento**

Quando selecionada, essa opção especifica que a caixa de diálogo **Abrir Arquivo** deve exibir o diretório do documento ativo. Quando essa opção está desmarcada, a caixa de diálogo **Abrir Arquivo** exibe o diretório que foi usado para abrir um arquivo pela última vez.

**Verificar terminações de linha consistentes ao carregar**

Selecione esta opção para que o editor verifique as terminações de linha em um arquivo e exiba uma caixa de mensagem se forem detectadas inconsistências na forma como as terminações de linha estão formatadas.

**Exibir aviso quando a opção de desfazer global for modificar arquivos editados**

Selecione esta opção para exibir uma caixa de mensagem quando o comando **Desfazer Global** for reverter alterações de refatoração feitas em arquivos que também foram alterados após a operação de refatoração. Retornar um arquivo ao seu estado pré-refatoração pode descartar alterações feitas posteriormente no arquivo.

**Mostrar arquivos diversos no Gerenciador de Soluções**

Selecione esta opção para exibir o nó **Arquivos Diversos** no **Gerenciador de Soluções**. Arquivos diversos são arquivos que não estão associadas um projeto ou solução, mas podem aparecer no **Gerenciador de Soluções** por questões de conveniência.

> [!NOTE]
> Selecione esta opção para ativar o comando **Exibir no navegador** no menu **Arquivo** para documentos da Web não incluídos no aplicativo web ativo.

**Itens salvos no projeto Arquivos diversos**

Especifica o número de arquivos a persistir na pasta **Arquivos diversos** do **Gerenciador de Soluções**. Esses arquivos são listados mesmo que não estejam mais abertos em um editor. É possível especificar qualquer número inteiro entre 0 e 256. O número padrão é 0.

Por exemplo, se você definir essa opção como 5 e tiver 10 arquivos diversos abertos, quando você fechar todos os 10 arquivos, os 5 primeiros ainda aparecerão na pasta **Arquivos Diversos**.

**Salvar documentos como Unicode quando os dados não puderem ser salvos em página de código**

Selecione esta opção para fazer com que arquivos que contêm informações incompatíveis com a página de código selecionada sejam salvos como Unicode por padrão.

## <a name="see-also"></a>Confira também

- [Arquivos Diversos](../../ide/reference/miscellaneous-files.md)
- [Localizando e substituindo texto](../../ide/finding-and-replacing-text.md)
