---
title: Desenvolver soluções do Office
description: Saiba como projetar um projeto usando as ferramentas de desenvolvedor do Office no Visual Studio. Saiba também como começar a implementar o código e a interface do usuário personalizada (UI).
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, about developing solutions
- solutions [Office development in Visual Studio], developing
- Office solutions [Office development in Visual Studio], developing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fbfe569e587c53aede6d550bc20527ad8d0fd328
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844992"
---
# <a name="develop-office-solutions"></a>Desenvolver soluções do Office
  Depois de projetar um projeto usando as ferramentas de desenvolvedor do Office no Visual Studio e configurar os arquivos de projeto, você pode começar a se concentrar na implementação do código e da interface do usuário personalizada (UI).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="office-solutions-programming-model"></a>Modelo de programação de soluções do Office
 O modelo de objeto do Office expõe uma variedade de objetos com os quais você pode programar. Sempre que você programar soluções do Office usando código gerenciado, escreverá código que usa tipos nos assemblies de interoperabilidade primária do Office. Em soluções que você cria usando os modelos de projeto do Office no Visual Studio, você também escreve o código diretamente em relação às classes geradas em seu projeto. Para obter mais informações, consulte [escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md).

## <a name="program-different-types-of-office-solutions"></a>Programar diferentes tipos de soluções do Office
 O tipo de solução que você está criando determina quais recursos você pode usar em seu projeto. Por exemplo, você pode adicionar controles de Windows Forms e controles estendidos do Office (chamados de *controles de host*) a personalizações em nível de documento arrastando itens da **caixa de ferramentas** no Visual Studio em tempo de design. No entanto, se você estiver desenvolvendo um suplemento do VSTO, só poderá adicionar esses tipos de controles a documentos em tempo de execução, escrevendo código.

 Para obter mais informações sobre os recursos específicos de diferentes tipos de soluções, consulte os seguintes tópicos:

- [Programe suplementos do VSTO](../vsto/programming-vsto-add-ins.md).

- [Programar personalizações em nível de documento](../vsto/programming-document-level-customizations.md).

- [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md).

  Para obter informações básicas para ajudá-lo a planejar suas soluções e procedimentos do Office para ajudá-lo a criar projetos, consulte Criar [soluções do Office](../vsto/designing-and-creating-office-solutions.md).

## <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----------|-----------------|
|[Escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md)|Descreve diferentes aspectos da gravação de código em soluções do Office.|
|[Programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md)|Fornece uma visão geral do modelo de programação de suplementos do VSTO e tarefas de programação relacionadas.|
|[Programar personalizações em nível de documento](../vsto/programming-document-level-customizations.md)|Fornece uma visão geral do modelo de programação de personalizações em nível de documento e tarefas de programação relacionadas.|
|[Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)|Descreve as diferentes maneiras pelas quais você pode personalizar a interface do usuário de aplicativos do Office usando suplementos do VSTO e personalizações no nível do documento.|
|[Dados em soluções do Office](../vsto/data-in-office-solutions.md)|Descreve as diferentes maneiras pelas quais você pode trabalhar com dados em soluções do Office, como associação de dados a controles e armazenamento em cache de dados em personalizações em nível de documento.|
|[Como o salvamento automático afeta as soluções do Office](./how-autosave-impacts-office-solutions.md)|Descreve os ajustes que talvez você precise fazer nas soluções do Office quando o salvamento automático estiver habilitado.|
|[Solucionar problemas de soluções do Office](../vsto/troubleshooting-office-solutions.md)|Fornece dicas para solucionar problemas comuns que você pode encontrar ao criar soluções do Office.|
|[Suporte a Threading no Office](../vsto/threading-support-in-office.md)|Fornece uma visão geral de como trabalhar com vários threads em soluções do Office.|
|[Acessibilidade em projetos do Office](../vsto/accessibility-in-office-projects.md)|Descreve os recursos de acessibilidade que estão disponíveis nas soluções do Office.|

## <a name="see-also"></a>Confira também
- [Como: criar e modificar propriedades de documento personalizadas](../vsto/how-to-create-and-modify-custom-document-properties.md)
- [Como: ler e gravar nas propriedades do documento](../vsto/how-to-read-from-and-write-to-document-properties.md)
- [Como: direcionar a interface do usuário multilíngüe do Office](../vsto/how-to-target-the-office-multilingual-user-interface.md)
- [Walkthrough: criar seu primeiro suplemento do VSTO para Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)
- [Walkthrough: criar sua primeira personalização em nível de documento para o Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)
- [Walkthrough: criar seu primeiro suplemento do VSTO para Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)
- [Walkthrough: criar seu primeiro suplemento do VSTO para PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [Walkthrough: criar seu primeiro suplemento do VSTO para o projeto](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)
- [Walkthrough: criar seu primeiro suplemento do VSTO para Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)
- [Walkthrough: criar sua primeira personalização em nível de documento para o Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)
