---
title: Suporte para configurações do usuário | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02bb2450196de76917e9cffc2f5f5acc6c8ee7b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704786"
---
# <a name="support-for-user-settings"></a>Suporte para configurações de usuário
Um VSPackage pode definir uma ou mais categorias de configurações, que são grupos de variáveis de estado que persistem quando um usuário escolhe o comando **Configurações de importação/exportação** no menu **Ferramentas.** Para habilitar essa persistência, você usa as [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]APIs de configuração no .

 Uma entrada de registro que é referida como um ponto de configurações personalizado e um GUID define a categoria configurações do VSPackage. Um VSPackage pode suportar várias categorias de configurações, cada uma definida por um ponto de configurações personalizado.

- Implementações de configurações baseadas em conjuntos <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> interop (usando a interface) devem criar ponto de configurações personalizados editando o registro ou usando um script registrador (arquivo.rgs). Para obter mais informações, consulte [Criando scripts de registrador](/cpp/atl/creating-registrar-scripts).

- O código que usa o MPF (Managed Package Framework, <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> estrutura de pacotes gerenciados) deve criar pontos de configurações personalizados anexando um ao VSPackage para cada ponto de configurações personalizados.

     Se um único VSPackage suportar vários pontos de configuração personalizados, cada ponto de configurações personalizados <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> será implementado por uma classe separada e cada um será registrado por uma instância única da classe. Consequentemente, uma classe de configurações que implementa pode suportar mais de uma categoria de configurações.

## <a name="custom-settings-point-registry-entry-details"></a>Detalhes de entrada do registro de ponto de configurações personalizadas
 Os pontos de configuração personalizados são criados em uma entrada de registro\\no seguinte local: `<CSPName>` HKLM\Software\Microsoft\VisualStudio*\<Versão>* \UserSettings\\`<CSPName>`, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]onde está o nome do Ponto de Configurações Personalizadas que o VSPackage suporta e * \<versão>* é a versão de , por exemplo 8.0.

> [!NOTE]
> O caminho raiz do HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Versão>* pode ser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] substituído por uma raiz alternativa quando o ambiente de desenvolvimento integrado (IDE) é inicializado. Para obter mais informações, consulte [Switches de linha de comando](../../extensibility/command-line-switches-visual-studio-sdk.md).

 A estrutura da entrada do registro é ilustrada abaixo:

 HKLM\Software\Microsoft\VisualStudio\\*\<Versão>* \UserSettings\

 `<CSPName`>= '#12345'

 Pacote = '{XXXXXX XXXX XXXX XXXX XXXXXXXXX}'

 Categoria = '{yyyyyy yyyy yyyy yyyyyyyyyyyyyy}'

 Pacote de recursos = '{ZZZZZZZZZZ ZZZZ ZZZZZZZZZZZZZZZZZZZ}'

 AlternateParent = CategoryName

| Nome | Type | Dados | Descrição |
|-----------------|--------| - | - |
| (Padrão) | REG_SZ | Nome do ponto de configurações personalizado | O nome da `<CSPName` chave,>, é o nome não localizado do Ponto de Configurações Personalizadas.<br /><br /> Para implementações baseadas no MPF, o nome da `categoryName` chave `objectName` é obtido <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> pela `categoryName_objectName`combinação dos argumentos e argumentos da construtora em .<br /><br /> A chave pode estar vazia, ou pode conter o ID de referência da seqüência localizada em um DLL de satélite. Esse valor é obtido `objectNameResourceID` a <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> partir do argumento para o construtor. |
| Pacote | REG_SZ | GUID | O GUID do VSPackage que implementa o Ponto de Configurações Personalizadas.<br /><br /> Implementações baseadas no <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> MPF utilizando a `objectType` classe, utilizem o <xref:System.Type> argumento do construtor contendo o VSPackage's e reflexão para obter esse valor. |
| Categoria | REG_SZ | GUID | GUIA identificando a categoria de configurações.<br /><br /> Para implementações baseadas em montagens interop, esse valor pode [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ser um GUID <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> arbitrariamente escolhido, que o IDE passa para os <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> métodos. Todas as implementações desses dois métodos devem verificar seus argumentos GUID.<br /><br /> Para implementações baseadas no MPF, este <xref:System.Type> GUID é obtido [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pela classe que implementa o mecanismo de configuração. |
| Pacote de recursos | REG_SZ | GUID | Opcional.<br /><br /> Caminho para dLL de satélite contendo strings localizadas se o VSPackage implementando não fornecê-los.<br /><br /> O MPF usa a reflexão para obter <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> o recurso correto VSPackage, para que a classe não defina esse argumento. |
| AlternateParent | REG_SZ | Nome da pasta na página Opções de ferramentas que contém este ponto de configurações personalizadas. | Opcional.<br /><br /> Você deve definir esse valor somente se uma implementação de configurações suportar páginas **de opções de ferramentas** que usam o mecanismo de persistência no [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] e não no mecanismo no modelo de automação para salvar o estado.<br /><br /> Nestes casos, o valor na tecla AlternateParent é a `topic` seção da `topic.sub-topic` string usada para identificar a página **Opções de ferramentas** em particular. Por exemplo, para a `"TextEditor.Basic"` página **ToolsOptions,** `"TextEditor"`o valor de AlternateParent seria .<br /><br /> Quando <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> gera o Ponto de Configurações Personalizadas, é o mesmo que o nome da categoria. |
