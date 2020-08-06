---
title: パッケージの再展開 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- redeploying packages [Integration Services]
- deploying packages [Integration Services], redeploying
ms.assetid: 86806efb-8cf4-4f9d-9824-1152cb4c495c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4c5286d406d96f62fc74eb619f7e7a6064fde2a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713270"
---
# <a name="redeployment-of-packages"></a>パッケージの再配置
  プロジェクトの配置後に、パッケージの機能を更新または拡張し、更新したパッケージを含む [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを再配置する必要がある場合があります。 パッケージの再配置プロセスの一環として、配置ユーティリティに含まれている構成プロパティを見直す必要があります。 たとえば、パッケージの再配置後に構成が変更されないようにする場合などがあります。  
  
## <a name="process-for-redeployment"></a>再配置のプロセス  
 パッケージの更新の終了後、プロジェクトを再構築し、ターゲット コンピューターに配置フォルダーをコピーしてから、パッケージ インストール ウィザードを再度実行します。  
  
 プロジェクトのパッケージの一部だけを更新した場合、プロジェクト全体を再配置する必要がないことがあります。 パッケージの一部だけを配置するために、新しい [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを作成して、このプロジェクトに更新したパッケージを追加し、プロジェクトをビルドして配置できます。 パッケージの構成は、パッケージを別のプロジェクトに追加する際に、自動的にパッケージと共にコピーされます。  
  
## <a name="related-tasks"></a>Related Tasks  
 [配置ユーティリティを使用してパッケージを配置する](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md)  
  
  
