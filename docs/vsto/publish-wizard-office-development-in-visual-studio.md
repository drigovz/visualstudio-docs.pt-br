---
title: Assistente de publicação (desenvolvimento do Office no Visual Studio)
description: Saiba como você pode usar o assistente de publicação para copiar arquivos de solução para um local especificado, criar os arquivos de manifesto e criar um programa de instalação no Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.PublishWizard
- VST.PublishWizard.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], Publish Wizard
- deploying applications [Office development in Visual Studio], Publish Wizard
- Office applications [Office development in Visual Studio], Publish Wizard
- Publish Wizard, Office solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 25821a0f245f2f0ed30fcbfb10137a772dd0dd01
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528016"
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>Assistente de publicação (desenvolvimento do Office no Visual Studio)
  Use o **Assistente de publicação** para copiar arquivos de solução para um local especificado, criar os arquivos de manifesto e criar um programa de instalação.

 Para acessar esse assistente, no menu **Compilar** , escolha **publicar** *SolutionName*. Você também pode acessar o **Assistente de publicação** do **Gerenciador de soluções**. Abra o menu de atalho para o nó do projeto e escolha **publicar**.

 Cada seção abaixo descreve uma página do assistente.

## <a name="where-do-you-want-to-publish-the-application"></a>Onde você deseja publicar o aplicativo?
 **Especifique o local para publicar este aplicativo** Necessário. O local de publicação é o diretório em que o **Assistente de publicação** copia os arquivos da solução, como manifestos, assemblies, certificado temporário e outros arquivos da compilação. Você deve ter acesso de gravação a esse diretório.

 Digite o local como um caminho de disco, compartilhamento de arquivos, site FTP ou URL do site ou clique no botão **procurar** para procurar o local. O caminho pode estar nestes formatos:

- Um caminho relativo ou absoluto no formato padrão do Windows, como *C:\deploy\myapplication* ou *\MyApplication*.

- Um caminho UNC (Convenção de nomenclatura universal), como *\\ \ServerName\MyApplication \\*.

- Uma URL de um site da Web, como `http://www.contoso.com/MyApplication` .

  Por padrão, o local de publicação é *http://localhost/projectname/* se você tiver o IIS instalado ou o diretório Publish \ se não tiver o IIS instalado.

> [!NOTE]
> Há mais considerações se o computador de destino estiver executando o Windows Vista. Você deve ser um administrador no computador com Windows Vista para usar a opção de publicação local. Além disso, o local padrão é sempre o diretório de *publicação \\* , independentemente de você ter o IIS instalado.

## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>Qual é o caminho de instalação padrão nos computadores dos usuários finais?
 O caminho de instalação é opcional. Você pode definir o caminho de instalação mais tarde, se preferir. Para obter detalhes, consulte [como alterar o caminho de instalação de uma solução do Office](/previous-versions/bb608626(v=vs.110)).

 O caminho de instalação é o diretório do qual o usuário final irá instalar a personalização. Ele também é o caminho que será usado pela solução para verificar se há atualizações. O **Assistente de publicação** não implantará a solução nesse local, a menos que o caminho seja o mesmo que você inseriu na caixa **especificar o local para publicar este aplicativo** na página anterior.

 **De um site da Web** Especifique a URL que os usuários finais seguirão para instalar a solução.

 **De um caminho UNC ou compartilhamento de arquivos** Especifique o caminho UNC que os usuários finais seguirão para instalar a solução.

 **De um CD-ROM ou DVD-ROM** Essa opção não requer um caminho de instalação.

 O Visual Studio não grava o CD ou DVD. Você deve copiar a saída para um CD ou DVD manualmente.

## <a name="see-also"></a>Veja também
- [Implantar uma solução do Office usando o ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Publicar página, designer de projeto &#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)
- [Implantar uma solução do Office](../vsto/deploying-an-office-solution.md)