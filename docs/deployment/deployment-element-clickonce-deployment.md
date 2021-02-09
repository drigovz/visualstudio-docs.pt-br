---
title: '&lt;&gt;elemento Deployment (implantação do ClickOnce) | Microsoft Docs'
description: O elemento de implantação identifica os atributos usados para a implantação de atualizações e a exposição ao sistema.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#subscription
- urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup
- urn:schemas-microsoft-com:asm.v2#deploymentProvider
- urn:schemas-microsoft-com:asm.v2#update
- urn:schemas-microsoft-com:asm.v2#deployment
- urn:schemas-microsoft-com:asm.v2#expiration
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <deployment> element [ClickOnce deployment manifest]
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 369d48c76ed82825021622af35141ef12ff42c76
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893900"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;&gt;elemento Deployment (implantação do ClickOnce)
Identifica os atributos usados para a implantação de atualizações e a exposição ao sistema.

## <a name="syntax"></a>Sintaxe

```xml

      <deployment
   install
   minimumRequiredVersion
   mapFileExtensions
   disallowUrlActivation
   trustUrlParameters
>
   <subscription>
         <update>
            <beforeApplicationStartup/>
            <expiration
               maximumAge
               unit
            />
         </update>
   </subscription>
   <deploymentProvider
      codebase
   />
</deployment>
```

## <a name="elements-and-attributes"></a>Elementos e atributos
 O `deployment` elemento é obrigatório e está no `urn:schemas-microsoft-com:asm.v2` namespace. O elemento tem os atributos a seguir.

| Atributo | Descrição |
|--------------------------| - |
| `install` | Obrigatórios. Especifica se este aplicativo define uma presença no menu **Iniciar** do Windows e no aplicativo **Adicionar ou remover programas** do painel de controle. Os valores válidos são `true` e `false`. Se `false` , [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o sempre executará a versão mais recente deste aplicativo da rede e não reconhecerá o `subscription` elemento. |
| `minimumRequiredVersion` | Opcional. Especifica a versão mínima deste aplicativo que pode ser executada no cliente. Se o número de versão do aplicativo for menor que o número de versão fornecido no manifesto de implantação, o aplicativo não será executado. Os números de versão devem ser especificados no formato `N.N.N.N` , em que `N` é um inteiro não assinado. Se o `install` atributo for `false` , `minimumRequiredVersion` não deve ser definido. |
| `mapFileExtensions` | Opcional. Assume o padrão de `false`. Se `true` , todos os arquivos na implantação devem ter uma extensão. Deploy. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o removerá essa extensão desses arquivos assim que eles forem baixados do servidor Web. Se você publicar seu aplicativo usando o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , ele adicionará automaticamente essa extensão a todos os arquivos. Esse parâmetro permite que todos os arquivos em uma [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação sejam baixados de um servidor Web que bloqueia a transmissão de arquivos que terminam em extensões "inseguras", como. exe. |
| `disallowUrlActivation` | Opcional. Assume o padrão de `false`. Se `true` , impede que um aplicativo instalado seja iniciado clicando na URL ou inserindo a URL no Internet Explorer. Se o `install` atributo não estiver presente, esse atributo será ignorado. |
| `trustURLParameters` | Opcional. Assume o padrão de `false`. Se `true` , permite que a URL contenha parâmetros de cadeia de caracteres de consulta que são passados para o aplicativo, assim como argumentos de linha de comando são passados para um aplicativo de linha de comando. Para obter mais informações, consulte [como recuperar informações de cadeia de caracteres de consulta em um aplicativo ClickOnce online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Se o `disallowUrlActivation` atributo for `true` , `trustUrlParameters` deve ser excluído do manifesto ou definido explicitamente como `false` . |

 O `deployment` elemento também contém os seguintes elementos filho.

## <a name="subscription"></a>subscription
 Opcional. Contém o `update` elemento. O `subscription` elemento não tem atributos. Se o `subscription` elemento não existir, o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo nunca verificará se há atualizações. Se o `install` atributo do `deployment` elemento for `false` , o `subscription` elemento será ignorado, pois um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo que é iniciado da rede sempre usa a versão mais recente.

## <a name="update"></a>atualizar
 Obrigatório. Esse elemento é um filho do `subscription` elemento e contém o `beforeApplicationStartup` `expiration` elemento ou. `beforeApplicationStartup` e `expiration` não podem ser especificados no mesmo manifesto de implantação.

 O `update` elemento não tem atributos.

## <a name="beforeapplicationstartup"></a>beforeApplicationStartup
 Opcional. Este elemento é um filho do `update` elemento e não tem atributos. Quando o `beforeApplicationStartup` elemento existir, o aplicativo será bloqueado ao [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verificar se há atualizações, se o cliente estiver online. Se esse elemento não existir, o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verificará primeiro se há atualizações com base nos valores especificados para o `expiration` elemento. `beforeApplicationStartup` e `expiration` não podem ser especificados no mesmo manifesto de implantação.

## <a name="expiration"></a>expiração
 Opcional. Este elemento é um filho do `update` elemento e não tem filhos. `beforeApplicationStartup` e `expiration` não podem ser especificados no mesmo manifesto de implantação. Quando a verificação de atualização ocorre e uma versão atualizada é detectada, a nova versão é armazenada em cache enquanto a versão existente é executada. A nova versão é instalada na próxima inicialização do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.

 O `expiration` elemento dá suporte aos seguintes atributos.

|Atributo|Descrição|
|---------------|-----------------|
|`maximumAge`|Obrigatórios. Identifica o quão antigo a atualização atual deve se tornar antes de o aplicativo executar uma verificação de atualização. A unidade de tempo é determinada pelo `unit` atributo.|
|`unit`|Obrigatório. Identifica a unidade de tempo para `maximumAge` . As unidades válidas são `hours` , `days` e `weeks` .|

## <a name="deploymentprovider"></a>deploymentProvider
 Para o .NET Framework 2,0, esse elemento será necessário se o manifesto de implantação contiver uma `subscription` seção. Para o .NET Framework 3,5 e posterior, esse elemento é opcional e será padronizado para o servidor e o caminho do arquivo no qual o manifesto de implantação foi descoberto.

 Esse elemento é um filho do `deployment` elemento e tem o atributo a seguir.

| Atributo | Descrição |
|------------| - |
| `codebase` | Obrigatórios. Identifica o local, como um Uniform Resource Identifier (URI), do manifesto de implantação que é usado para atualizar o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo. Esse elemento também permite o encaminhamento de locais de atualização para instalações baseadas em CD. Deve ser um URI válido. |

## <a name="remarks"></a>Comentários
 Você pode configurar seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo para verificar se há atualizações na inicialização, verificar se há atualizações após a inicialização ou nunca verificar se há atualizações. Para verificar se há atualizações na inicialização, verifique se o `beforeApplicationStartup` elemento existe no `update` elemento. Para verificar se há atualizações após a inicialização, verifique se o `expiration` elemento existe no `update` elemento e se os intervalos de atualização são fornecidos.

 Para desabilitar a verificação de atualizações, remova o `subscription` elemento. Ao especificar no manifesto de implantação para nunca verificar se há atualizações, você ainda pode verificar manualmente se há atualizações usando o <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> método.

 Para obter mais informações sobre como o deploymentProvider está relacionado a atualizações, consulte [escolhendo uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

## <a name="examples"></a>Exemplos
 O exemplo de código a seguir ilustra um `deployment` elemento em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto de implantação. O exemplo usa um `deploymentProvider` elemento para indicar o local de atualização preferencial.

```xml
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">
    <subscription>
      <update>
        <expiration maximumAge="6" unit="hours" />
      </update>
    </subscription>
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />
  </deployment>
```

## <a name="see-also"></a>Confira também
- [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)