---
title: Validar o sistema durante o desenvolvimento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams
ms.assetid: c9dafb47-7b1d-4c72-9432-d43be3db1799
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1beeef572282a642e4a989086ac0fd228409fec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "82586276"
---
# <a name="validate-your-system-during-development"></a>Validar o sistema durante o desenvolvimento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O Visual Studio pode ajudar a manter seu software consistente com os requisitos dos usuários e com a arquitetura do seu sistema.

 Para ver quais versões do Visual Studio oferecem suporte a cada um desses recursos, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Tarefas-chave
 Use as tarefas a seguir para validar o software.

|**Tarefas**|**Tópicos associados**|
|---------------|---------------------------|
|**Verifique se seu modelo é consistente:**<br /><br /> Dependendo da maneira como seu projeto usa e interpreta modelos, pode ser útil não permitir algumas combinações de elementos. Por exemplo, você pode restringir as classes UML para que elas sempre tenham [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] nomes em conformidade. Você pode definir restrições como essas em [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] extensões.|-   [Validar seu modelo UML](../modeling/validate-your-uml-model.md)<br />-   [Definir restrições de validação para modelos UML](../modeling/define-validation-constraints-for-uml-models.md)|
|**Verifique se o software atende aos requisitos dos usuários**:<br /><br /> Você pode usar requisitos e modelos arquitetônicos para ajudá-lo a organizar os testes do seu sistema e seus componentes. Essa prática ajuda a garantir que você teste os requisitos que são importantes para os usuários e outros participantes e ajuda a atualizar os testes rapidamente quando os requisitos mudam.|-   [Desenvolver testes de um modelo](../modeling/develop-tests-from-a-model.md)|
|**Certifique-se de que seu software permaneça consistente com o design pretendido do seu sistema:**<br /><br /> Os diagramas de camada descrevem as dependências pretendidas entre os componentes do seu aplicativo. Durante o desenvolvimento, você pode verificar se as dependências reais no código estão em conformidade com o design pretendido.|-   [Crie diagramas de camada do seu código](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Validar o código com diagramas de camada](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Recursos externos

|**Categoria**|**Links**|
|------------------|---------------|
|**Vídeos**|![link para o canal de vídeo](../data-tools/media/playvideo.gif "PlayVideo") [9: Doug sete: compreensão de código e design do sistema com o Visual Studio 2010](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![link para o canal de vídeo](../data-tools/media/playvideo.gif "PlayVideo") [9: Arquitetando um aplicativo usando um diagrama de camada](https://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-5-Architecting-an-Application)<br /><br /> ![link para vídeo](../data-tools/media/playvideo.gif "PlayVideo") [série How do MSDN: como validar o código usando diagramas de camada](https://msdn.microsoft.com/vstudio/gg501755)|
|**Fóruns**|-   [Ferramentas de modelagem & de visualização do Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [SDK de modelagem de & de visualização do Visual Studio (ferramentas DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Blogs**|-   [Blog do Visual Studio ALM + Team Foundation Server](https://devblogs.microsoft.com/devops/welcome-to-the-visual-studio-alm-team-foundation-server-blog/)|
|**Artigos técnicos e diários**|[Centro de arquitetura do MSDN](https://msdn.microsoft.com/architecture/default.aspx)|

## <a name="see-also"></a>Consulte Também
 [Testando o aplicativo](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac) [estender modelos UML e diagramas](../modeling/extend-uml-models-and-diagrams.md) [modelo requisitos de usuário](../modeling/model-user-requirements.md) [análise e arquitetura de modelagem](../modeling/analyze-and-model-your-architecture.md)
