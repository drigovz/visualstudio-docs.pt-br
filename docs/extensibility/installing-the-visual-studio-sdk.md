---
title: Instalando o SDK do Visual Studio | Microsoft Docs
description: Saiba mais sobre as opções para instalar o kit de desenvolvimento de software do Visual Studio, incluindo durante a instalação do Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 07/12/2018
ms.topic: overview
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f5b0d239c2280362b45c085448437b15bd8ddfe8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869525"
---
# <a name="install-the-visual-studio-sdk"></a>Instalar o SDK do Visual Studio

O SDK do Visual Studio (Software Development Kit) é um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instalar o SDK do Visual Studio como parte de uma instalação do Visual Studio

Para incluir o SDK do VS em sua instalação do Visual Studio, instale a carga de trabalho de **desenvolvimento da extensão do Visual Studio** em **outros conjuntos de ferramentas**. Essa carga de trabalho instalará o SDK do Visual Studio e os pré-requisitos necessários. Você pode ajustar a instalação selecionando ou desmarcando componentes da exibição de **Resumo** .

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Instalar o SDK do Visual Studio depois de instalar o Visual Studio

Para instalar o SDK do Visual Studio após concluir a instalação do Visual Studio, execute novamente o instalador do Visual Studio e selecione a carga de trabalho de **desenvolvimento da extensão do Visual Studio** .

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Instalar o SDK do Visual Studio de uma solução

Se você abrir uma solução com um projeto de extensibilidade sem primeiro instalar o SDK do VS, será solicitada uma caixa de diálogo **instalar recurso ausente** para instalar a carga de trabalho de **desenvolvimento da extensão do Visual Studio** :

![Instalar o desenvolvimento da extensão](../extensibility/media/install-extension-development.png "Instalar o desenvolvimento da extensão")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Instalar o SDK do Visual Studio a partir da linha de comando

Como com qualquer carga de trabalho ou componente do Visual Studio, você também pode instalar a carga de trabalho de **desenvolvimento de extensão do Visual Studio** (ID: Microsoft. VisualStudio. Workload. VisualStudioExtension) na linha de comando. Consulte [usar parâmetros de linha de comando para instalar o Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) para obter detalhes sobre as opções de linha de comando apropriadas e instruções gerais sobre como determinar a carga de trabalho ou os identificadores de componente.

Observe que você deve usar o instalador do Visual Studio que corresponde à sua versão instalada do Visual Studio. Por exemplo, se você tiver Visual Studio Enterprise instalado em seu computador, deverá executar o instalador do Visual Studio Enterprise (*vs_enterprise.exe*).
