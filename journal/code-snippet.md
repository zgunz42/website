---
date: 2021-07-11
author: Nichlas W. Andersen
title: Code Snippet
excerpt: kegiatana makan

---
Something along the lines of

    const migrationConfigs = [
    {
        directory: ['db/commonMigrations', 'db/schema1Migrations'],
        tableName: 'schema1_migrations',
        schemaName: 'schema1',
    },
    
    {
        directory: ['db/commonMigrations', 'db/schema2Migrations'],
        tableName: 'schema2_migrations',
        schemaName: 'schema2',
    }
    ]
    
        for (let config of migrationConfigs) {
          await knex.raw(`CREATE SCHEMA IF NOT EXISTS ${config.schemaName}`)
          await knex.migrate.latest(config)
    }
    

Are you confident about approach you are taking, though? Duplicating entire table structure just for localization purposes sounds weird; or datasets are actually different based on locale?