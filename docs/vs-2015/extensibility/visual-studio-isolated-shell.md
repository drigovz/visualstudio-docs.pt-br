---
title: Shell isolado do Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications%2C isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications%2C isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ef2d1cbffab5e38e603b0e50beb896f1c6efa23d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75919198"
---
# <a name="visual-studio-isolated-shell"></a>Shell isolado do Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O Shell isolado do Visual Studio permite que você crie aplicativos autônomos que podem ser executados lado a lado com outras versões do Visual Studio. Ele é usado principalmente para hospedar ferramentas especializadas que podem usar os serviços do Visual Studio, mas também ter uma aparência e marca personalizadas. Os recursos do Visual Studio e os grupos de comandos de menu podem ser ativados e desativados facilmente. Os títulos de aplicativos, os ícones de aplicativos e as telas de abertura são totalmente personalizáveis. Para obter uma lista de recursos personalizáveis, consulte [Personalizando o Shell isolado](../extensibility/customizing-the-isolated-shell.md).  
  
 Para trabalhar com um projeto de shell isolado, você deve instalar o SDK do Visual Studio. A partir do Visual Studio 2015, você não instala o SDK do Visual Studio a partir do centro de download. Ele é incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalando o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Para criar um aplicativo de shell isolado, comece com um projeto isolado do shell do Visual Studio. Este projeto contém tudo o que você precisa para desenvolver e testar seu próprio aplicativo de shell isolado. Quando estiver pronto para escrever o programa de instalação que implanta seu aplicativo, você deverá obter o pacote redistribuível do Shell isolado de [shell do Microsoft Visual Studio (isolado) pacote redistribuível](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/).  
  
> [!NOTE]
> Antes de poder acessar o pacote redistribuível do Shell isolado, você será solicitado a preencher uma breve pesquisa do cliente.  Depois de preencher a pesquisa, você será direcionado para uma página do Visual Studio Connect com links de download de pacote redistribuível.  Você pode encontrar os links de download em visitas posteriores ao site do Visual Studio Connect **, na guia programas &#124; Visual Studio 2015 do Shell integrado e isolado** .  
  
> [!NOTE]
> Para obter mais informações sobre como implantar um aplicativo baseado em shell isolado, consulte [Walkthrough: Criando um aplicativo de shell isolado básico](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="working-with-the-isolated-shell"></a>Trabalhando com o Shell isolado  
 Um aplicativo de shell isolado do Visual Studio tem acesso completo aos serviços do Visual Studio e dá suporte a personalização e identidade visual especiais. Há várias maneiras de personalizar um aplicativo de shell isolado:  
  
- Você pode usar as partes de componente VSPackages e Managed Extensibility Framework (MEF) para estender um aplicativo de shell isolado exatamente como você os usaria em qualquer outra extensão do Visual Studio. Para obter mais informações, consulte [estendendo o Shell isolado](../extensibility/extending-the-isolated-shell.md).  
  
- Para tornar os recursos do Visual Studio e os grupos de comandos de menu disponíveis ou indisponíveis, atualize o arquivo. vsct no projeto de interface do usuário (IU) do aplicativo.  
  
- Para remover as páginas de **Opções** ou outros componentes do shell do Visual Studio do aplicativo, atualize o arquivo. pkgundef do aplicativo.  
  
- Para modificar outros aspectos da aparência ou comportamento do Shell, atualize o arquivo. pkgdef do aplicativo.  
  
- Alguns aspectos do Shell também podem ser especificados quando o aplicativo é iniciado. Para fazer isso, atualize os parâmetros na chamada para o ponto de entrada inicial do appenvstub.dll.  
  
  Para obter mais informações sobre os diferentes elementos que você pode personalizar, consulte [elementos do Shell isolado](../extensibility/elements-of-the-isolated-shell.md).  
  
## <a name="standard-features-of-the-isolated-shell"></a>Recursos padrão do Shell isolado  
 Os recursos a seguir são padrão para todas as edições do Visual Studio.  
  
|Categoria de Recurso|Recurso|  
|----------------------|-------------|  
|Recursos do IDE|Configurações de importação/exportação<br /><br /> Instalador de controle de caixa de ferramentas<br /><br /> Lista de Tarefas & Lista de Erros<br /><br /> Janela de saída<br /><br /> Start Page<br /><br /> Janela Propriedades<br /><br /> Caixa de Ferramentas<br /><br /> Gerenciador de Soluções<br /><br /> Janela de Indicadores<br /><br /> Exibição de Classe<br /><br /> Pesquisador de Objetos<br /><br /> Janela Comando<br /><br /> Estrutura de Tópicos do Documento<br /><br /> Modo de Exibição de Recursos<br /><br /> Ferramenta externa<br /><br /> Windows Communication Foundation (WCF) Adicionar Referência de Serviço<br /><br /> Suporte para LINQ (consulta integrada à linguagem)|  
|Editor/Designer|Ferramentas de navegação de código (localização unificada, definição de origem, herança)<br /><br /> IntelliSense<br /><br /> SmartTag<br /><br /> Gerenciador de Snippets de Código<br /><br /> Snippets de código<br /><br /> Refatoração<br /><br /> Lista de estilos<br /><br /> Filtragem do IntelliSense<br /><br /> Janela de definição de código<br /><br /> Designer de aplicativos<br /><br /> Designer de Formulários do Windows<br /><br /> Designer de Windows Presentation Foundation (WPF)|  
|Depuração|Avaliador de expressão C#<br /><br /> Depuração local<br /><br /> Depuração gerenciada<br /><br /> Editar e continuar<br /><br /> Depuração entre threads<br /><br /> Visualizações<br /><br /> DataTips<br /><br /> Depuração nativa<br /><br /> Depuração de scripts<br /><br /> Depuração de interoperabilidade<br /><br /> Depuração Just-in-time (JIT)<br /><br /> Depuração de vários processos<br /><br /> Depuração de XSLT<br /><br /> Anexar ao processo local<br /><br /> Pontos de rastreamento<br /><br /> Restrições de ponto de interrupção|  
|Dados|Gerenciador de Servidores (somente dados simplificados)<br /><br /> Associação de dados a dados locais (. MDF ou. MDB<br /><br /> Vinculação de dados ao objeto<br /><br /> Associação de dados ao serviço Web<br /><br /> Conjunto completo de controles de dados<br /><br /> Editor de XML<br /><br /> Ligação de dados com o servidor de banco local<br /><br /> janela Fontes de Dados|  
|Web|Editor de HTML<br /><br /> Navegador da Web<br /><br /> O Web Forms designer<br /><br /> Projeto de site<br /><br /> Projeto de aplicativo Web|  
|Extensibilidade|Consome componentes VSPackages e MEF|  
  
## <a name="see-also"></a>Consulte Também  
 [Shell (isolado ou integrado)](../extensibility/shell-isolated-or-integrated.md)
