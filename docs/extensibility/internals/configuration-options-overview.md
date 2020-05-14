---
title: Visão geral das opções de configuração | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d5ac25fcef7b942b791402baf17982c9810e92a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709406"
---
# <a name="configuration-options-overview"></a>Visão geral das opções de configuração
Os [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projetos podem suportar várias configurações que podem ser construídas, depuradas, executadas e/ou implantadas. Uma configuração é um tipo de compilação descrito com um conjunto de propriedades nomeada, tipicamente comum switches de compilador e locais de arquivo. Por padrão, novas soluções contêm duas configurações, *Debug* e *Release*. Essas configurações podem ser aplicadas usando suas configurações padrão ou modificadas para atender aos requisitos específicos da solução e/ou do projeto. Alguns pacotes podem ser construídos de duas maneiras: como um editor ActiveX ou como um componente no lugar. No entanto, os projetos não precisam suportar múltiplas configurações. Se houver apenas uma configuração disponível, essa configuração será mapeada em todas as configurações da solução.

 As configurações geralmente consistem em duas partes: o nome de configuração (como *Debug* ou *Release)* e as configurações da plataforma. O nome da plataforma de uma configuração identifica o ambiente que a configuração tem como alvo, como um conjunto de API ou uma plataforma de sistema operacional. Os [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usuários não podem criar uma plataforma; eles devem escolher entre as seleções que um projeto VSPackage permite. Quando um usuário instala um VSPackage, a plataforma de entrega criada durante o desenvolvimento do pacote pode surgir qualquer nome de plataforma desejado com base em quaisquer critérios definidos pelo criador do pacote. O usuário pode então selecionar a lista de plataformas disponibilizadas através do VSPackage quando as páginas de propriedade são instanciadas.

 Os nomes das plataformas são opcionais, já que nem todos os projetos suportam o conceito de plataformas. Quando uma configuração não tem um nome de plataforma, a string **N/A** é exibida na ui.

 Cada solução tem seu próprio conjunto de configurações, apenas uma das quais pode estar ativa por vez. Uma configuração de solução é um conjunto de não mais do que uma configuração de cada projeto. A estipulação "não mais do que" deve-se à opção de excluir um projeto de uma configuração de solução. Os usuários podem criar suas próprias configurações de solução personalizadas.

 A tabela a seguir ilustra a configuração de configurações típicas de um projeto. As linhas são rotuladas com nomes de configuração e colunas com nomes de plataforma.

|Nome da configuração|Plataforma: Win32|Plataforma: Win64|
|------------------------|----------------------|----------------------|
|*Depuração*|\<Debug Win32 configurações>|\<Depurar configurações do Win64>|
|*Versão*|\<Liberar configurações do Win32>|\<Versie as configurações do Win64>|
|*MyConfig*|N/D|\<Configurações do MyConfig Win64>|

> [!NOTE]
> Não é possível criar uma configuração de solução *MyConfig* que exclua uma plataforma Win32, a menos que o projeto que você está mirando não suporte o Win32.

 Alterar a configuração ativa de uma solução seleciona o conjunto de configurações do projeto que é construído, executado, depurado ou implantado nessa solução. Por exemplo, se você alterar a configuração da solução ativa de *Release* para *Debug,* todos os projetos dentro dessa solução serão automaticamente construídos com a configuração dos projetos indicada na configuração de depuração da solução. As configurações dos projetos também são chamadas *de Debug,* a menos que o usuário tenha feito alterações manuais no Gerenciador de Configuração do ambiente.

 As propriedades de configuração da solução armazenadas para cada projeto incluem o nome do projeto, nome da configuração do projeto, sinalizadores para indicar se devem ou não ser implantados e o nome da plataforma. Para obter mais informações, consulte [configuração da solução](../../extensibility/internals/solution-configuration.md).

 O usuário pode visualizar e definir parâmetros de configuração da solução selecionando a solução na hierarquia (Solution Explorer) e abrindo as páginas de propriedade. Da mesma forma, você pode visualizar e definir parâmetros de configuração do projeto selecionando um projeto no Solution Explorer e abrindo as páginas de propriedade para esse projeto.

 O usuário também pode construir um projeto usando configurações de configuração de versão e todo o resto com configurações de configuração de depuração, se necessário. Para obter mais informações, consulte [a configuração do projeto para construção](../../extensibility/internals/project-configuration-for-building.md).

 O diagrama a seguir mostra como as interfaces que suportam configurações de soluções e projetos são implementadas:

 ![Gráfico de interfaces de configuração](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces") Interfaces de configuração

 Algumas notas relativas ao diagrama anterior:

- `IDispatch`é marcado como opcional no objeto de configuração. Especificamente, é opcional ter as interfaces de configuração no objeto de navegação.

- `IVsDebuggableProjectCfg`é marcado como opcional no objeto de configuração, mas é necessário para o suporte de depuração.

- `IVsProjectCfg2`é marcado como opcional no objeto de configuração, mas é necessário para o suporte ao agrupamento de saídas.

- O objeto Provedor de configuração é marcado como um objeto opcional, mas a opção é onde implementá-lo. Você pode implementar o objeto no objeto do projeto ou em um objeto separado.

- `IVsCfgProvider2`é necessário para o suporte da plataforma e edição de configuração. `IVsCfgProvider`é suficiente se você não implementar essa funcionalidade.

- Alguns desses objetos mostrados no diagrama como objetos separados podem ser combinados na mesma classe onde práticos com base em seus requisitos específicos de design. Em outros tópicos desta seção, no entanto, os objetos e interfaces associados a esses objetos serão discutidos de acordo com o cenário apresentado no diagrama.

- Certos objetos são implementados separadamente. Por exemplo, a construção de projetos e soluções ocorre em segmentos separados e o objeto para gerenciar as vidas de compilação separadamente do objeto que descreve a configuração para a compilação.

  Para obter mais informações sobre as interfaces de objeto de configuração e as interfaces de objeto do provedor de configuração no diagrama anterior, consulte [Objeto de configuração do Projeto](../../extensibility/internals/project-configuration-object.md). Além disso, [a configuração do Projeto para construção](../../extensibility/internals/project-configuration-for-building.md) fornece mais informações sobre o construtor de configuração e as interfaces de objeto de dependência de compilação e a [configuração do Projeto para gerenciamento de implantação](../../extensibility/internals/project-configuration-for-managing-deployment.md) descreve ainda mais as interfaces anexadas ao implantador de configuração e aos objetos de dependência de implantação de implantação. Finalmente, [a configuração do projeto para saída](../../extensibility/internals/project-configuration-for-output.md) descreve as interfaces de objeto de grupo de saída e saída e o uso de páginas de propriedade para exibir e definir propriedades dependentes da configuração.

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>
- [Configuração do projeto para construção](../../extensibility/internals/project-configuration-for-building.md)
- [Configuração da solução](../../extensibility/internals/solution-configuration.md)
