---
name: shopify-dev
description: >-
  Uses the Shopify Dev MCP server and official tools to assist with Shopify app, theme, and extension development.
---

# Shopify Development Skill

This skill provides you with guidelines and context for developing on Shopify. It utilizes the `@shopify/dev-mcp` Model Context Protocol (MCP) server which gives you direct access to Shopify's documentation, GraphQL schemas, and tooling right from this workspace.

## Best Practices
- **Use the MCP Server**: Whenever you need to look up documentation or validate code, utilize the tools provided by the `shopify-dev` MCP server.
- **Shopify CLI**: The primary CLI tool for interacting with Shopify is `shopify`. Use commands like `shopify theme dev` or `shopify app dev` when running or previewing projects.
- **Liquid**: Follow Shopify's Liquid guidelines for templates. Remember to check schemas and data types properly.
- **GraphQL**: When interacting with the Shopify Admin API, use GraphQL whenever possible, as it is Shopify's recommended API structure.

## Capabilities Enabled
- Access to official Shopify Developer Documentation.
- Code validation and syntax references for Liquid and Shopify APIs.
- Schema browsing for the Storefront and Admin GraphQL APIs.
