---
title: Visão geral da integração de controle de fonte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d80363286f5f0cac9a5ceb2e8ac9d20345df9e6f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705117"
---
# <a name="source-control-integration-overview"></a>Visão geral da integração do controle do código-fonte
Esta seção compara as duas maneiras de integrar-se ao controle de origem do Visual Studio; um plug-in de controle de origem e um VSPackage que fornece uma solução de controle de origem e destaca os novos recursos de controle de origem. O Visual Studio permite a troca manual entre o controle de origem VSPackages e plug-ins de controle de origem, bem como a comutação automática baseada em soluções.

## <a name="source-control-integration"></a>Integração de controle do código-fonte
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]suporta dois tipos de opções de integração de controle de origem. Em todas [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]as versões de, você ainda pode integrar um plug-in baseado na API plug-in de controle de fonte (anteriormente também referida como API MSSCCI), que fornece funcionalidade básica de controle de origem ao usar a interface de usuário de controle de fonte do Visual Studio (UI). Um controle de origem VSPackage, por outro lado, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] fornece um novo caminho de integração profunda adequado para a integração de controle de origem que exige um alto nível de sofisticação e autonomia em seu modelo de controle de origem.

 ![Visão geral do controle de fonte](../../extensibility/internals/media/sourcectnrloverview.gif "Visão geral do SourceCtnrl")

## <a name="source-control-plug-in"></a>Plug-in de controle de origem
 Todas as versões do Visual Studio suportam a especificação de API plug-in de controle de fonte versão 1.2 como um caminho de integração. Um implementador plug-in de controle de origem grava uma DLL que implementa as funções de API plug-in de controle de fonte para integração e registro de controle de origem, conforme descrito no [Creating a Source Control Plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md). Nesta abordagem, o Ambiente de Desenvolvimento [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Integrado (IDE) usa a ui para caixas de diálogo, como check-in, check-out, páginas de propriedades de ferramentas/opções, barras de ferramentas e glifos de controle de origem. A adesão rigorosa à API plug-in de controle de origem garante uma fácil integração ao Visual Studio e uma experiência sem problemas para o usuário. Isso significa que o plug-in de controle de origem deve implementar a maioria das funções e retornos de chamada detalhados na API.

 Para implementar um plug-in de controle de origem usando a API plug-in de controle de origem, siga estas etapas:

1. Crie uma DLL que implemente as funções especificadas nos [Plug-ins de controle de fonte](../../extensibility/source-control-plug-ins.md).

2. Registre o DLL fazendo as entradas de registro apropriadas (descritas em [Como: Instalar um Plug-in de Controle de Origem](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)).

3. Crie uma im e uma ims e exibição do helper quando solicitado pelo Pacote adaptador de controle de fonte (o componente do Visual Studio que lida com a funcionalidade de controle de origem através de plug-ins de controle de origem)

   Em resposta a um comando de controle de origem, o Visual Studio IDE apresenta uma ui padrão para as operações básicas e, em seguida, passa as informações para o plug-in de controle de origem através das funções definidas na API plug-in de controle de fonte. Para opções avançadas, o plug-in de controle de origem pode ser chamado para apresentar sua própria ui, por exemplo, navegando por um projeto controlado por origem. Isso significa que o usuário pode ser apresentado com dois estilos possivelmente diferentes de IU ao lidar com o controle de origem: a UI que o Visual Studio apresenta e a UI que o plug-in de controle de origem apresenta. Isso é mais perceptível com operações avançadas de controle de fonte.

### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Desvantagens em implementar um plug-in de controle de origem

- Para recursos avançados, o usuário pode ver dois estilos diferentes de interfaces, levando a possíveis confusão.

- O plug-in de controle de origem está confinado ao modelo de controle de origem implícito pela API plug-in de controle de origem.

- A API plug-in de controle de origem pode ser muito restritiva para alguns cenários de controle de origem.

### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Vantagens em implementar um plug-in de controle de origem

- O Visual Studio fornece toda a ui para todas as operações básicas de controle de origem para que o plug-in de controle de origem não precise implementar a ui potencialmente complexa.

- Devido à API rigorosa, o plug-in de controle de origem pode interagir facilmente com programas externos de controle de fonte para fornecer funcionalidade mais extensa; O Visual Studio não se importa muito com a forma como a funcionalidade de controle de origem é realizada, apenas que ela é realizada de acordo com a API plug-in de controle de fonte.

- É mais fácil implementar um plug-in de controle de origem do que um vsPackage de controle de origem.

## <a name="source-control-vspackage"></a>Controle de origem VSPackage
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]permite uma profunda integração no Visual Studio com controle total da funcionalidade de controle de fonte e substituição completa da interface de usuário de controle de fonte fornecida pelo Visual Studio. Um controle de origem VSPackage é registrado no Visual Studio e fornece funcionalidade de controle de origem. Embora vários vsPackages de controle de origem possam ser registrados no Visual Studio, apenas um deles pode estar ativo a qualquer momento. Um controle de origem VSPackage tem controle total sobre a funcionalidade de controle de origem e aparência no Visual Studio enquanto ele está ativo. Todos os outros vsPacotes de controle de origem que podem ser registrados no sistema estão inativos e não exibirão nenhuma ui.

 Implementar um controle de origem VSPackage requer uma estratégia de "tudo ou nada". O criador de um controle de origem VSPackage deve investir uma quantidade significativa de esforço na implementação de uma série de interfaces de controle de fonte e novos elementos de Interface de Interface (caixas de diálogo, menus e barras de ferramentas) para cobrir toda a funcionalidade de controle de origem. Consulte [Criando um Pacote DE Controle de Origem VSPara](../../extensibility/internals/creating-a-source-control-vspackage.md) obter mais detalhes.

### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Desvantagens em implementar um vspackage de controle de origem

- O VSPackage deve implementar uma série de interfaces complexas para se integrar com sucesso ao Visual Studio.

- O VSPackage deve fornecer toda a iu necessária para o controle de origem; O Visual Studio não prestará assistência nesta área.

- Um controle de origem VSPackage está intimamente vinculado ao Visual Studio e não pode operar com programas autônomos, portanto, a funcionalidade não pode ser tão facilmente compartilhada com uma versão externa do programa de controle de origem.

### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Vantagens para implementar um vspackage de controle de origem

- Como o VSPackage tem controle total sobre a interface de usuário e funcionalidade do controle de origem, o usuário é apresentado com uma interface perfeita para controle de origem.

- O VSPackage não se limita a um modelo específico de controle de origem.

## <a name="see-also"></a>Confira também
- [Controle de Origem](../../extensibility/internals/source-control.md)
- [Criando um plug-in de controle do código-fonte](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Criar um VSPackage de controle do código-fonte](../../extensibility/internals/creating-a-source-control-vspackage.md)
- [Novidades no controle do código-fonte](../../extensibility/internals/what-s-new-in-source-control.md)
