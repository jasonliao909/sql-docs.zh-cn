---
title: STContains（geography 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- STContains method (geography)
ms.assetid: b10e8f0a-2926-449a-82ea-be42543420ca
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: c5947d1793b39a0bf6aba9729b9f4b1ca7305fab
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2020
ms.locfileid: "68042462"
---
# <a name="stcontains--geography-data-type"></a>STContains（geography 数据类型）
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  指定调用 geography 实例在空间上是否包含传递给该方法的 geography 实例   。  
  
## <a name="syntax"></a>语法  
  
```  
  
.STContains ( other_geography )  
```  
  
## <a name="arguments"></a>参数  
 other_geography   
 与对其调用  **的实例进行比较的其他 geography 实例**`STContains()`。  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：bit   
  
 CLR 返回类型：SqlBoolean   
  
## <a name="remarks"></a>备注  
 如果调用 geography 实例在空间上包含传递给该方法的 geography 实例，则返回 1；否则，返回 0   。 如果两个 geography 实例的 SRID 不同，则返回 null   。  
  
## <a name="examples"></a>示例  
 以下示例使用 `STContains()` 测试两个 `geography` 实例，以查看第一个实例是否包含第二个实例。  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::Parse('CURVEPOLYGON (COMPOUNDCURVE (CIRCULARSTRING (-122.200928 47.454094, -122.810669 47.00648, -122.942505 46.687131, -121.14624 45.786679, -119.119263 46.183634), (-119.119263 46.183634, -119.273071 47.107523, -120.640869 47.569114, -122.200928 47.454094)))');  
SET @h = geography::Parse('POINT(-121.703796 46.893985)');  
```  
  
 `SELECT @g.STContains(@h);`  
  
  
