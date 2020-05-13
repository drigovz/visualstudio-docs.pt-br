---
title: Essenciais do serviço de linguagem legado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 501bccf755293e86e8a9dc23fce125a10c882376
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707418"
---
# <a name="legacy-language-service-essentials"></a>Conceitos básicos do serviço de linguagem herdado
Você deve fornecer um serviço de idiomas para integrar uma linguagem de programação no Visual Studio. Este tópico explica os recursos disponíveis em serviços de idioma legado.

 Os serviços de linguagem legados são implementados como parte de um VSPackage, mas a maneira mais nova de implementar recursos de serviço de idioma é usar extensões MEF. Para saber mais sobre a nova maneira de implementar um serviço de idiomas, consulte [Editor e Language Service Extensions](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Recomendamos que você comece a usar a Nova API do editor o mais rápido possível. Isso melhorará o desempenho do seu serviço de idiomas e permitirá que você aproveite os novos recursos do editor.

 Os serviços de idioma legado fornecem os seguintes recursos:

|Recurso|Descrição|
|-------------|-----------------|
|Coloração de sintaxe|Faz com que a visualização do editor exiba diferentes cores e estilos de fonte para os diferentes elementos de uma linguagem. Essa diferenciação pode facilitar a leitura e a edição de arquivos.<br /><br /> Para obter informações gerais, consulte [Coloração de Sintaxe em um serviço de linguagem legado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Para obter informações sobre esse recurso no framework de pacote gerenciado (MPF), consulte [Sintaxdimensionar colorir em um serviço de linguagem legado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|
|Conclusão da instrução|Completa uma declaração ou palavra-chave que o usuário começou a digitar. A conclusão da declaração ajuda os usuários a inserir declarações difíceis mais facilmente, com menos digitação e menos chances de erro.<br /><br /> Para obter informações gerais, consulte [Conclusão da declaração em um serviço de linguagem legado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Para obter informações sobre esse recurso no MPF, consulte [Conclusão do Word em um serviço de linguagem legado](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|
|Correspondência de chaves|Destaca personagens emparelhados, como aparelhos. Quando o usuário digita um caractere de fechamento como "}", a correspondência de chaves destaca o caractere de abertura correspondente, como "{". Quando há vários níveis de caracteres de fechamento, esse recurso ajuda os usuários a confirmar que os caracteres de fechamento são emparelhados corretamente.<br /><br /> Para obter informações sobre esse recurso no MPF, consulte [Brace Matching em um serviço de linguagem legado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|
|Dicas de ferramentas de informações de parâmetros|Exibe uma lista de possíveis assinaturas para o método sobrecarregado que o usuário está digitando no momento.<br /><br /> Para obter informações gerais, consulte [Parameter Info em um serviço de linguagem legado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Para obter informações sobre esse recurso no MPF, consulte [Parâmetro Sinfonado em um Serviço de Linguagem Legado](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|
|Marcadores de erro|Exibe um sublinhado vermelho ondulado, também conhecido como squiggly, em texto que é sintáticamente incorreto. Marcadores de erro geralmente são usados para conscientizar os usuários sobre palavras-chave mal escritas, parênteses não fechados, caracteres inválidos e erros semelhantes.<br /><br /> Nas classes mpf, os marcadores de erro <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> são <xref:Microsoft.VisualStudio.Package.AuthoringSink> tratados automaticamente no método da classe.|

 Muitos desses recursos exigem o serviço de idioma para analisar o código fonte. Muitas vezes você pode reutilizar o código de tokenização e análise para o seu compilador ou intérprete.

 Os seguintes recursos estão relacionados ao suporte a linguagens de programação, mas não fazem parte dos serviços de idiomas:

| Recurso | Descrição |
|-----------------------| - |
| Avaliadores de expressão | Suporta o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador validando pontos de interrupção e fornecendo uma lista de expressões a serem exibidas na janela de depuração **Autos.**<br /><br /> Para obter mais informações, consulte [o suporte ao serviço de idiomas para depuração](../../extensibility/internals/language-service-support-for-debugging.md). |
| Ferramentas de navegação por símbolos | Suporta **navegador de objeto,** **visualização de classe,** **navegador de chamadas**e resultados de **símbolos**. |
