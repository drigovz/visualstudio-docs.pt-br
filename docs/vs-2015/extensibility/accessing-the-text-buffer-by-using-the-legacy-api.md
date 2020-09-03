---
title: Acessando o buffer de texto usando a API herdada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f2cfbd84bc4f9298358a2a2d1ba87f76d6e5303c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184997"
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>Acessar o buffer de texto usando a API herdada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O texto é responsável por gerenciar fluxos de texto e persistência de arquivo. Embora o buffer possa ler ou gravar outros formatos, toda a comunicação comum com o buffer é executada usando Unicode. Nas APIs herdadas, o buffer de texto pode usar um sistema de coordenadas de um ou dois dimensional para identificar os locais de caracteres no buffer.  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>Sistemas de coordenadas de uma e duas dimensões  
 Uma posição de coordenada unidimensional é baseada na posição de um caractere do primeiro caractere no buffer, como 147. Você usa a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> interface para acessar um local unidimensional no buffer. Um sistema de coordenadas bidimensional é baseado em pares de linha e índice. Por exemplo, um caractere no buffer em 43, 5 estaria na linha 43, cinco caracteres à direita do primeiro caractere nessa linha. Você acessa um local bidimensional no buffer usando a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interface. As <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> interfaces e são implementadas pelo objeto de buffer de texto ( <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> ) e podem ser acessadas umas das outras usando `QueryInterface` . O diagrama a seguir mostra essas e outras interfaces-chave no <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> .  
  
 ![Objeto de buffer de texto](../extensibility/media/vstextbuffer.gif "vsTextBuffer")  
Objeto de buffer de texto  
  
 Embora o sistema de coordenadas funcione no buffer de texto, ele é otimizado para usar coordenadas bidimensionais. Um sistema de coordenadas unidimensional pode criar uma sobrecarga de desempenho. Portanto, use o sistema de coordenadas bidimensional sempre que possível.  
  
 A segunda responsabilidade do buffer de texto é a persistência de arquivo. Para fazer isso, o objeto de buffer de texto implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> e atua como o componente de objeto de dados de documento para itens de projeto e outros componentes de ambiente envolvidos em persistência. Para obter mais informações, consulte [abrindo e salvando itens de projeto](../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Alterando as configurações de exibição usando a API herdada](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Explica como alterar as configurações de exibição usando a API herdada.  
  
 [Usando o gerenciador de texto para monitorar as configurações globais](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Explica como usar o Gerenciador de texto para monitorar as configurações globais.  
  
## <a name="see-also"></a>Consulte Também  
 [Dentro do editor principal](../extensibility/inside-the-core-editor.md)
