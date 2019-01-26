---
title: 'Como: Adicionar controles XMLNodes a documentos do Word'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9d754d7be732931cf3d50cf28db396b5040e3874
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870185"
---
# <a name="how-to-add-xmlnodes-controls-to-word-documents"></a>Como: Adicionar controles XMLNodes a documentos do Word
  **Importante** as informações que propus neste tópico sobre o Microsoft Word são desenvolver ou apresentadas exclusivamente para o uso e benefício de indivíduos e organizações que estão localizados fora dos Estados Unidos e seus territórios ou que estão usando o programas que são executados em produtos do Microsoft Word que foram licenciados pela Microsoft antes de janeiro de 2010, quando a Microsoft removido uma implementação da funcionalidade específica relacionada para XML personalizado do Microsoft Word. Essas informações sobre o Microsoft Word não podem ser lidas ou usadas por indivíduos ou organizações nos Estados Unidos ou em seus territórios de quem estão usando ou desenvolver programas que são executados em produtos do Microsoft Word que foram licenciados pela Microsoft depois de 10 de janeiro de 2010 ; Esses produtos não se comportará como produtos licenciados antes dessa data ou adquirido e licenciado para uso fora dos Estados Unidos.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Quando você mapeia um elemento repetido de esquema XML para um documento do Microsoft Office Word, o Visual Studio adiciona automaticamente um <xref:Microsoft.Office.Tools.Word.XMLNodes> controle ao documento.  
  
 Para obter informações sobre como mapear os elementos do esquema XML não-repetição, consulte [como: Adicionar controles XMLNode a documentos do Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).  
  
> [!NOTE]  
>  O <xref:Microsoft.Office.Tools.Word.XMLNodes> controle não está disponível na **caixa de ferramentas** ou o **fontes de dados** janela, nem pode ela ser criada por meio de programação.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-an-xmlnodes-control-to-a-document"></a>Para adicionar um controle do XMLNodes a um documento  
  
1.  No documento no designer do Visual Studio, na faixa de opções, clique o **desenvolvedor** guia.  
  
    > [!NOTE]  
    >  Se o **desenvolvedor** guia não estiver visível, você deve primeiro Mostrar. Para obter mais informações, confira [Como: Mostrar a guia Desenvolvedor na faixa de opções](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
2.  No **XML** , clique em **esquema**.  
  
     O **modelos e suplementos** caixa de diálogo é aberta.  
  
3.  Clique o **esquema XML** guia.  
  
4.  Clique em **adicionar esquema**.  
  
     O **adicionar esquema** caixa de diálogo é aberta.  
  
5.  Selecione um esquema XML que contém elementos do esquema de repetição e clique em **aberto**.  
  
     O **configurações de esquema** caixa de diálogo é exibida.  
  
6.  Atribuir um alias ou clique em **Okey** para adicionar o esquema sem um alias.  
  
     O esquema é adicionado para o **adicionar esquema** caixa de diálogo.  
  
7.  No **adicionar esquema** caixa de diálogo, clique em **Okey**.  
  
     O **estrutura XML** é aberto o painel de tarefas.  
  
8.  Clique no elemento do esquema de repetição na **estrutura XML** painel de tarefas para adicioná-lo ao documento.  
  
     Um <xref:Microsoft.Office.Tools.Word.XMLNodes> controle é criado e adicionado ao projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Controle XMLNodes](../vsto/xmlnodes-control.md)   
 [Automatizar o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Visão geral dos controles de host e de itens de host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
