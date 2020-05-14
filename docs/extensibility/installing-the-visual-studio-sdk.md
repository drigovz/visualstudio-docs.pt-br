---
title: Instalando o Visual Studio SDK | Microsoft Docs
ms.date: 07/12/2018
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f391708abbd8a9b66f2dfd5aaa6559cb075910d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710343"
---
# <a name="install-the-visual-studio-sdk"></a>Instalar o SDK do Visual Studio

O Visual Studio SDK (Software Development Kit) é um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instale o Visual Studio SDK como parte de uma instalação do Visual Studio

Para incluir o VS SDK em sua instalação do Visual Studio, instale a carga de trabalho de desenvolvimento de **extensão do Visual Studio** em **Outros conjuntos de ferramentas**. Esta carga de trabalho instalará o Visual Studio SDK e os pré-requisitos necessários. Você pode ajustar ainda mais a instalação selecionando ou dessindoinando componentes da exibição **Resumo.**

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Instale o Visual Studio SDK depois de instalar o Visual Studio

Para instalar o Visual Studio SDK após concluir sua instalação do Visual Studio, execute o instalador do Visual Studio e selecione a carga de **trabalho de desenvolvimento de extensão do Visual Studio.**

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Instale o Visual Studio SDK a partir de uma solução

Se você abrir uma solução com um projeto de extensibilidade sem antes instalar o VS SDK, você será solicitado por uma caixa de diálogo **Instalar recurso ausente** para instalar a carga de trabalho de desenvolvimento de **extensão do Visual Studio:**

![Instalar desenvolvimento de extensão](../extensibility/media/install-extension-development.png "Instalar desenvolvimento de extensão")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Instale o Visual Studio SDK a partir da linha de comando

Como em qualquer carga de trabalho ou componente do Visual Studio, você também pode instalar a carga de trabalho de desenvolvimento de **extensão do Visual Studio** (ID: Microsoft.VisualStudio.Workload.VisualStudioExtension) da linha de comando. Veja [Usar parâmetros de linha de comando para instalar](../install/use-command-line-parameters-to-install-visual-studio.md) o Visual Studio para obter detalhes sobre os switches de linha de comando apropriados e instruções gerais sobre como determinar a carga de trabalho ou identificadores de componentes.

Observe que você deve usar o instalador visual studio que corresponde à sua versão instalada do Visual Studio. Por exemplo, se você tiver o Visual Studio Enterprise instalado no seu computador, você deve executar o instalador Visual Studio Enterprise *(vs_enterprise.exe).*
