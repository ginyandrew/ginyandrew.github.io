---
title: Basic
layout: default
parent: Vue JS
nav_order: 1
---

# Vue - Basic 
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Vue Life Cycle

1. Creation : before Component is added to DOM / can't access to this.$el
	* beforeCreate - data/events are not set up yet, can't access to them
	* created - now can access to data/event 
2. Mounting 
	* beforeMount
	* mounted
3. Updating
	* beforeUpdate
4. Descruction
	* beforeDestroy
	* destroyed
