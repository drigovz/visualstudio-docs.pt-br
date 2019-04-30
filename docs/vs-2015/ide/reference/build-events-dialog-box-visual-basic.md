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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5eb4473056e8d9c42fedf781ed0f5d1189f42fca
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442654"
---
# <a name="build-events-dialog-box-visual-basic"></a>Caixa de diálogo de Eventos de Build (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use a caixa de diálogo **Eventos de Build** para especificar as instruções de configuração de build. Você também pode especificar as condições sob as quais eventos de pré-build ou de pós-build são executados. Para obter mais informações, confira [Como: Especificar eventos de build (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).  
  
 **Linha de comando do evento de pré-build**  
 Especifica comandos serem executados antes do início do build. Para digitar comandos longos, clique em **Editar Pré-Build** para exibir a [Caixa de Diálogo Linha de Comando de Evento de Pré-Build/Evento de Pós-Build](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).  
  
> [!NOTE]
> Eventos de pré-build não serão executados se o projeto estiver atualizado e nenhum build será disparado.  
  
 **Linha de comando de evento de pós-build**  
 Especifica comandos a serem executados após o fim do build. Para digitar comandos longos, clique em **Editar Pós-Build** para exibir a **Caixa de Diálogo Linha de Comando de Evento de Pré-Build/Evento de Pós-Build**.  
  
> [!NOTE]
> Adicione uma instrução `call` antes de todos os comandos pós-build que executam arquivos .bat. Por exemplo `call C:\MyFile.bat` ou `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
 **Executar o evento de pós-build**  
 Especifica as condições para o evento de pós-build ser executado, conforme mostrado na tabela a seguir.  
  
|Opção|Resultado|  
|------------|------------|  
|**Sempre**|O evento de pós-build será executado independentemente de o build ser bem-sucedido.|  
|**No build bem-sucedido**|O evento de pós-build será executado se o build for bem-sucedido. O evento será executado mesmo para um projeto atualizado, desde que o build seja bem-sucedido. Essa é a configuração padrão.|  
|**Quando o build atualizar a saída do projeto**|O evento de pós-build só será executado quando o arquivo de saída do compilador (.exe ou .dll) for diferente do arquivo de saída anterior do compilador. Um evento de pós-build não será executado se um projeto for atualizado.|  
  
## <a name="see-also"></a>Consulte também  
 [Página de Compilação, Designer de Projeto (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)   
 [Como: Especificar eventos de Build (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)   
 [Caixa de diálogo da linha de comando do evento de pré-build/evento de pós-build](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
