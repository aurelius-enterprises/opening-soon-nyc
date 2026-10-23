# Opening Soon NYC

New liquor licence applications across New York City, by borough, a few weeks before the doors open.

Source: New York State Liquor Authority data via data.ny.gov (Current SLA Pending Licenses, dataset
`f8i8-k2gm`, joined with the active licences dataset `9s3h-dpkz`), published under the OPEN-NY terms of use.
Opening Soon NYC is not affiliated with the New York State Liquor Authority. An application is not an opening.

Compiled automatically from New York State Liquor Authority data via data.ny.gov. Not affiliated with the SLA.
Names are shown only for business entities; individuals' names are withheld.

Pages: `index.html`, one per borough (7-day window; 30 days for Queens, the Bronx and Staten Island),
`licensed.html` (newly licensed on-premises venues, seven days behind), `weekly/<ISO-week>.html`,
`feed.xml` (Atom), `sitemap.xml`, `robots.txt`. `BASE_URL` in `src/render.py` is a placeholder until the rename.

## Rebuild

The pages are static HTML with relative links and no build step on the host (`.nojekyll` turns off Jekyll).
They are generated from the pipeline that lives next to this directory:

```
python3 src/pipeline.py      # fetch today's snapshot and diff from data.ny.gov
python3 src/render.py        # write site/*.html and site/.nojekyll from the newest snapshot
python3 src/audit_site.py    # name and footer checks; must report no failures
```

Copy the contents of `site/` to the root of the Pages branch to publish.
