---
title: 'Práticas recomendadas de desenvolvimento: COM, VSTO, & suplementos do VBA no Office'
ms.date: 07/25/2017
ms.topic: conceptual
dev_langs:
- ''
helpviewer_keywords:
- ''
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d5dd8864484e2b41a1146f1da495251663afdb6a
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801497"
---
# <a name="development-best-practices-for-com-vsto-and-vba-add-ins-in-office"></a>Práticas recomendadas de desenvolvimento para os suplementos COM, VSTO e VBA no Office
  Se você estiver desenvolvendo suplementos COM, VSTO ou VBA para Office, siga as práticas recomendadas de desenvolvimento descritas neste artigo.   Isso ajuda a garantir que:

- Compatibilidade dos seus suplementos em diferentes versões e implantações do Office.
- Complexidade reduzida da implantação de suplemento para seus usuários e administradores de ti.
- A instalação não intencional ou falhas de tempo de execução do seu suplemento não ocorrem.

>Observação: não há suporte para a utilização da [ponte de desktop](/windows/uwp/porting/desktop-to-uwp-root) para preparar seu suplemento com, VSTO ou VBA para a Windows Store. Os suplementos do COM, VSTO e VBA não podem ser distribuídos na Windows Store ou na Office Store.

## <a name="do-not-check-for-office-during-installation"></a>Não verificar o Office durante a instalação
 Não recomendamos que o seu suplemento detecte se o Office está instalado durante o processo de instalação do suplemento. Se o Office não estiver instalado, você poderá instalar o suplemento e o usuário poderá acessá-lo após a instalação do Office.

## <a name="use-embedded-interop-types-nopia"></a>Usar tipos de interoperabilidade inseridos (NoPIA)
Se sua solução usar o .NET 4,0 ou posterior, use os tipos de interoperabilidade incorporados (NoPIA) em vez de, dependendo dos assemblies de interoperabilidade do Office Primary Interop (PIA). Usar a inserção de tipo reduz o tamanho da instalação da sua solução e garante a compatibilidade futura. O Office 2010 foi a última versão do Office que lançou o PIA redistribuível. Para obter mais informações, consulte [Walkthrough: inserindo informações de tipo de assemblies de Microsoft Office](https://msdn.microsoft.com/library/ee317478.aspx) e [tipos de interoperabilidade inserido e tipo de equivalência](/windows/uwp/porting/desktop-to-uwp-root).

Se sua solução usar uma versão anterior do .NET, recomendamos que você atualize sua solução para usar o .NET 4,0 ou posterior. Usar o .NET 4,0 ou posterior reduz os pré-requisitos de tempo de execução em versões mais recentes do Windows.

## <a name="avoid-depending-on-specific-office-versions"></a>Evitar dependendo das versões específicas do Office
Se sua solução usar a funcionalidade disponível apenas nas versões mais recentes do Office, verifique se a funcionalidade existe (se possível, no nível de recurso) em tempo de execução (por exemplo, usando manipulação de exceção ou verificando a versão). Valide as versões mínimas, em vez de versões específicas, usando APIs com suporte no modelo de objeto, como a [Propriedade Application. Version](<xref:Microsoft.Office.Interop.Excel._Application.Version%2A>). Não recomendamos que você confie nos metadados binários do Office, nos caminhos de instalação ou nas chaves do registro, pois eles podem mudar entre instalações, ambientes e versões.

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>Habilitar o uso do Office de 32 bits e de 64 bits
Seu destino de compilação padrão deve dar suporte a 32 bits (x86) e 64 bits (x64), a menos que sua solução dependa de bibliotecas que estão disponíveis somente para um determinado bit de bits. A versão de 64 bits do Office está aumentando em adoção, especialmente em ambientes Big Data. Dar suporte a 32 bits e 64 bits torna mais fácil para os usuários fazer a transição entre as versões de 32 bits e de 64 bits do Office.

Ao escrever código do VBA, use instruções de declaração segura de 64 bits e converta as variáveis conforme apropriado. Além disso, verifique se os documentos podem ser compartilhados entre os usuários que executam versões de 32 bits ou 64 bits do Office, fornecendo o código para cada bit de bits. Para obter mais informações, consulte [visão geral de Visual Basic de 64 bits para aplicativos](/office/vba/Language/Concepts/Getting-Started/64-bit-visual-basic-for-applications-overview).

## <a name="support-restricted-environments"></a>Suporte a ambientes restritos
Sua solução não deve exigir privilégios de administrador ou elevação de conta de usuário. Além disso, a solução não deve depender da configuração ou alteração:

- O diretório de trabalho atual.
- Diretórios de carregamento de DLL.
- A variável PATH.

## <a name="change-the-save-location-of-shared-data-and-settings"></a>Alterar o local de salvamento de dados e configurações compartilhadas
Se a solução consistir em um suplemento e um processo externo ao Office, não use a pasta de dados de aplicativo do usuário ou o registro para trocar dados ou configurações entre o suplemento e o processo externo. Em vez disso, considere usar a pasta temporária do usuário, a pasta documentos ou o diretório de instalação da solução.

## <a name="increment-the-version-number-with-each-update"></a>Incrementar o número de versão com cada atualização
Defina o número de versão dos binários em sua solução e aumente-o com cada atualização. Isso facilitará para os usuários identificarem as alterações entre as versões e avaliar a compatibilidade.

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>Fornecer instruções de suporte para as versões mais recentes do Office
Os clientes estão solicitando que os ISVs forneçam instruções de suporte para seus suplementos COM, VSTO e VBA que são executados no Office. A listagem de suas instruções explícitas de suporte ajuda os clientes que usam aplicativos Microsoft 365 para ferramentas de preparação para empresas a compreender o seu suporte.

Para fornecer instruções de suporte para aplicativos cliente do Office (por exemplo, Word ou Excel), primeiro verifique se os suplementos são executados na versão atual do Office e, em seguida, confirme para fornecer atualizações se o seu suplemento for interrompido em uma versão futura. Você não precisa testar seus suplementos quando a Microsoft lança uma nova compilação ou uma atualização para o Office. A Microsoft raramente altera a plataforma de extensibilidade COM, VSTO e VBA no Office, e essas alterações serão bem documentadas.

>Importante: a Microsoft mantém uma lista de suplementos com suporte para relatórios de preparação e informações de contato de ISV. Para obter o suplemento listado, consulte [/ConfigMgr/desktop-Analytics/Ready-for-Windows](/configmgr/desktop-analytics/ready-for-windows).

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>Use o Process Monitor para ajudar a depurar problemas de instalação ou de carregamento
Se o seu suplemento tiver problemas de compatibilidade durante a instalação ou carga, eles poderão estar relacionados a problemas com o acesso ao arquivo ou ao registro. Use o [Monitor de processos](/sysinternals/downloads/procmon) ou uma ferramenta de depuração semelhante para registrar e comparar o comportamento em um ambiente de trabalho para ajudar a identificar o problema.
