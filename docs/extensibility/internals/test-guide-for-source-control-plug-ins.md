---
title: Guia de teste para plug-ins de controle de origem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6b3f8e76e977472a3459697a650b32dae657c22
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704383"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Guia de teste para plug-ins de controle do código-fonte
Esta seção fornece orientação para testar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]seu plug-in de controle de origem com . Uma ampla visão geral das áreas de teste mais comuns, bem como algumas das áreas mais complexas que podem ser problemáticas, é fornecida. Esta visão geral não se destina a ser uma lista exaustiva de casos de teste.

> [!NOTE]
> Algumas correções de bugs [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e melhorias no IDE mais recente podem descobrir problemas com plug-ins de controle de origem existentes que não foram encontrados anteriormente durante o uso de versões anteriores de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. É fortemente recomendável que você teste seu plug-in de controle de origem existente para as áreas enumeradas nesta seção, mesmo que não tenham sido feitas alterações no plug-in desde a versão anterior de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="common-preparation"></a>Preparação Comum
 Uma máquina [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] com e o plug-in de controle de origem de destino instalado, é necessário. Uma segunda máquina configurada da mesma forma pode ser usada para alguns dos testes Open from Source Control.

## <a name="definition-of-terms"></a>Definição de Termos
 Para efeitos deste guia de teste, use as seguintes definições de termo:

 Projeto cliente Qualquer tipo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de projeto disponível que [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]suporte [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]a [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]integração de controle de origem (por exemplo, ou ).

 Projeto web Existem quatro tipos de projetos web: Sistema de Arquivos, IIS Local, Sites Remotos e FTP.

- Os projetos do Sistema de Arquivos são criados em um caminho local, mas não exigem que os Serviços de Informação da Internet (IIS) sejam instalados, pois são acessados internamente por meio de um caminho UNC, e podem ser colocados sob controle de origem de dentro do IDE, assim como projetos de clientes.

- Os projetos iis locais funcionam com o IIS que é instalado na mesma máquina e é acessado com uma URL apontando para a máquina local.

- Os projetos de Sites remotos também são criados sob um Serviço IIS, mas são [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] colocados sob controle de origem na máquina de servidor IIS e não de dentro do IDE.

- Os projetos ftp são acessados através de um servidor FTP remoto, mas não podem ser colocados sob controle de origem.

  Alistamento Outro termo para a solução ou projeto sob controle de origem.

  Version Store O banco de dados de controle de origem que está sendo acessado através da API plug-in de controle de fonte.

## <a name="test-areas-covered-in-this-section"></a>Áreas de teste cobertas nesta seção

- [Área de teste 1: Adicionar/abrir do controle de origem](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

  - Caso 1a: Adicionar solução ao controle de origem

  - Caso 1b: Solução aberta do controle de origem

  - Caso 1c: Adicionar solução do controle de origem

- [Área de teste 2: obter do controle do código-fonte](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [Área de teste 3: Check Out/Undo Checkout](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

  - Caso 3: Check Out/Undo Checkout

  - Caso 3A: Confira

  - Caso 3b: Checkout desconectado

  - Caso 3c: Consulta Edit/Query Save (QEQS)

  - Caso 3d: Checkout silencioso

  - Caso 3e: Desfazer checkout

- [Área de teste 4: fazer check-in](../../extensibility/internals/test-area-4-check-in.md)

  - Caso 4a: Itens modificados

  - Caso 4b: Adicionando arquivos

  - Caso 4c: Adicionando projetos

- [Área de teste 5: alterar o controle do código-fonte](../../extensibility/internals/test-area-5-change-source-control.md)

  - Caso 5a: Vincular

  - Caso 5b: Desvincular

  - Caso 5c: Revinculação

- [Área de teste 6: excluir](../../extensibility/internals/test-area-6-delete.md)

- [Testar área 7: compartilhar](../../extensibility/internals/test-area-7-share.md)

- [Área de teste 8: alternância de plug-in](../../extensibility/internals/test-area-8-plug-in-switching.md)

  - Caso 8a: Mudança Automática

  - Caso 8b: Alteração baseada em solução

## <a name="see-also"></a>Confira também
- [Plug-ins de controle do código-fonte](../../extensibility/source-control-plug-ins.md)
