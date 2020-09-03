---
title: Caixa de diálogo Eventos de Build (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- build events, specifying
- pre-build events
- Build Events dialog box
- post-build events
ms.assetid: 3a81a7c7-39f9-47a8-ba5a-b351227f380e
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9fa3b4365f49d172e077ca132b26a49580228c25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660953"
---
# <a name="build-events-dialog-box-visual-basic"></a>Caixa de diálogo de Eventos de Build (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use a caixa de diálogo **Eventos de Build** para especificar as instruções de configuração de build. Você também pode especificar as condições sob as quais eventos de pré-build ou de pós-build são executados. Para obter mais informações, consulte [Como especificar eventos de build (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

 **Linha de comando do evento de pré-build** Especifica os comandos a serem executados antes do início do build. Para digitar comandos longos, clique em **Editar Pré-Build** para exibir a [Caixa de Diálogo Linha de Comando de Evento de Pré-Build/Evento de Pós-Build](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> Eventos de pré-build não serão executados se o projeto estiver atualizado e nenhum build será disparado.

 **Linha de comando do evento de pós-build** Especifica os comandos a serem executados após o término do build. Para digitar comandos longos, clique em **Editar pós-compilação** para exibir a caixa de comando de evento de **pré-compilação evento/pós-compilação linha d**ialog.

> [!NOTE]
> Adicione uma instrução `call` antes de todos os comandos pós-build que executam arquivos .bat. Por exemplo, `call C:\MyFile.bat` ou `call C:\MyFile.bat call C:\MyFile2.bat`.

 **Executar o evento de pós-build** Especifica as condições para que o evento de pós-build seja executado, conforme é mostrado na tabela a seguir.

|Opção|Result|
|------------|------------|
|**Always**|O evento de pós-build será executado independentemente de o build ser bem-sucedido.|
|**Na compilação bem-sucedida**|O evento de pós-build será executado se o build for bem-sucedido. O evento será executado mesmo para um projeto atualizado, desde que o build seja bem-sucedido. Essa é a configuração padrão.|
|**Quando o build atualizar a saída do projeto**|O evento de pós-build só será executado quando o arquivo de saída do compilador (.exe ou .dll) for diferente do arquivo de saída anterior do compilador. Um evento de pós-build não será executado se um projeto for atualizado.|

## <a name="see-also"></a>Consulte Também
 [Página de compilação, designer de projeto (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) como especificar a caixa de diálogo evento de pré-compilação [de eventos de compilação (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md) [/linha de comando de evento de pós-compilação](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
