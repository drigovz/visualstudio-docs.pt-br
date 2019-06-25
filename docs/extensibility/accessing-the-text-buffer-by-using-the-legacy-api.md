---
title: Acessando o Buffer de texto usando a API herdada | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 661bf39e82fef5c040861bc9386dcb7f897d25cb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313622"
---
# <a name="access-the-text-buffer-by-using-the-legacy-api"></a>Acessar o buffer de texto, usando a API herdada
O texto é responsável por gerenciar os fluxos de texto e persistência de arquivo. Embora o buffer pode ler ou gravar outros formatos, toda a comunicação comum com o buffer é executada usando o Unicode. Nas APIs herdadas, o buffer de texto pode usar aquele - ou um sistema de coordenadas bidimensional para identificar os locais de caractere no buffer.

## <a name="one--and-two-dimension-coordinate-systems"></a>Dimensão de um e dois sistemas de coordenadas
 Uma posição de coordenadas unidimensional baseia-se a posição de um caractere a partir do primeiro caractere no buffer, como 147. Você usa o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> interface para acessar um unidimensional local no buffer. Um sistema de coordenadas bidimensional é baseado em pares de linha e índice. Por exemplo, um caractere no buffer em 43, 5 seria na linha 43, cinco caracteres à direita do primeiro caractere na linha. Você acessa um local bidimensional no buffer usando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interface. Tanto a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> e o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> interfaces são implementadas pelo objeto de buffer de texto (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>) e pode ser acessado entre si usando `QueryInterface`. O diagrama a seguir mostra essas e outras interfaces principais em <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.

 ![Objeto de Buffer de texto](../extensibility/media/vstextbuffer.gif "vsTextBuffer") objeto de buffer de texto

 Embora o sistema de coordenadas funcione no buffer de texto, ele é otimizado para usar coordenadas bidimensionais. Um sistema de coordenadas unidimensional pode criar sobrecarga de desempenho. Portanto, use o sistema de coordenadas bidimensional sempre que possível.

 O responsabilidade de segundo do buffer de texto é a persistência de arquivo. Para fazer isso, o objeto de buffer de texto implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> e atua como o componente de objeto de dados de documentos para itens de projeto e outros componentes do ambiente envolvidos na persistência. Para obter mais informações, consulte [abrindo e salvando itens de projeto](../extensibility/internals/opening-and-saving-project-items.md).

## <a name="in-this-section"></a>Nesta seção
- [Alterar configurações de exibição usando a API herdada](../extensibility/changing-view-settings-by-using-the-legacy-api.md) explica como alterar as configurações de exibição usando a API herdada.

- [Use o Gerenciador de texto para monitorar as configurações globais](../extensibility/using-the-text-manager-to-monitor-global-settings.md) explica como usar o Gerenciador de texto para monitorar as configurações globais.

## <a name="see-also"></a>Consulte também
- [Dentro do editor de núcleo](../extensibility/inside-the-core-editor.md)