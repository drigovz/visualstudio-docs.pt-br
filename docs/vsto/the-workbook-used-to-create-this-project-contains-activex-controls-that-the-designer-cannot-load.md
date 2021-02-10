---
title: A pasta de trabalho contém controles ActiveX que não podem ser carregados
description: Saiba como você pode resolver o erro que ocorre quando uma pasta de trabalho contém controles ActiveX que não podem ser carregados.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: error-reference
f1_keywords:
- VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4c8039fc2a5df197446873f0b2efef82d9a5f662
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940781"
---
# <a name="the-workbook-contains-activex-controls-that-cannot-be-loaded"></a>A pasta de trabalho contém controles ActiveX que não podem ser carregados

  O erro "a pasta de trabalho usada para criar este projeto contém controles ActiveX que o designer não pode carregar" aparece quando você adiciona um controle a um documento do Word ou uma planilha do Excel de forma programática, salva o documento ou a pasta de trabalho e, em seguida, cria uma nova solução de nível de documento com base no documento ou na pasta de trabalho.

 As informações que descrevem o tipo gerenciado do controle não são salvas junto com o documento ou a pasta de trabalho. Quando você cria uma nova solução com base no documento ou pasta de trabalho, o Visual Studio não tem informações suficientes para carregar o controle no designer de item de host.

## <a name="to-correct-this-error"></a>Para corrigir este erro

1. Abra o documento ou pasta de trabalho.

2. Remova os controles que foram adicionados em tempo de execução. Você pode fazer isso selecionando-os no documento ou na pasta de trabalho e pressionando a tecla **delete** .

3. Crie uma solução de nível de documento com base no documento ou na pasta de trabalho.

## <a name="see-also"></a>Confira também
- [Como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)
