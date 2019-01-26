---
title: A pasta de trabalho usada para criar este projeto contém controles ActiveX que o designer não pode carregar
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d8c42a1d1a6745daca8d83d3f21916253e70fdae
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867436"
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>A pasta de trabalho usada para criar este projeto contém controles ActiveX que o designer não pode carregar
  Este erro aparece quando você adiciona um controle a um documento do Word ou uma planilha do Excel programaticamente, salve o documento ou pasta de trabalho e, em seguida, crie uma nova solução de nível de documento com base no documento ou pasta de trabalho.  
  
 Informações que descrevem o tipo gerenciado do controle não é salva com o documento ou pasta de trabalho. Quando você cria uma nova solução com base nesse documento ou pasta de trabalho, o Visual Studio não tem informações suficientes para carregar o controle no designer de item de host.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Abra o documento ou pasta de trabalho.  
  
2.  Remova os controles que foram adicionados em tempo de execução. Você pode fazer isso, selecionando-os no documento ou pasta de trabalho e pressionar o **excluir** chave.  
  
3.  Crie uma solução de nível de documento com base no documento ou pasta de trabalho.  
  
## <a name="see-also"></a>Consulte também  
 [Como: Criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)  
