# The double-ITCZ project

This project provide a ladder of Python notebooks taking undergraduates with no coding background from
"here is what rain looks like" to the longest-standing systematic error in
climate modelling.

---

## Quick start 

You will run these in **VS Code**. You don't  need to install anything on your laptop.

1. Make a **GitHub account** with your FSU email at `github.com`.
2. Claim **student benefits** at `education.github.com` → "Get student benefits".
   Do this early — verification can take a day.
3. Open this repository, click the green **`< > Code`** button → **Codespaces**
   tab → **Create codespace on main**.
4. Wait two or three minutes while it builds and installs the libraries.
5. Open **`00_observed_rainfall.ipynb`**, click **Select Kernel** (top right) →
   **Python Environments** → **Python 3.11**.
6. Run the *Check your setup* cell. It should print "all good".
7. Start reading. Work top to bottom, and **answer the "Your turn" boxes** —
   they are the assignment, not decoration.

Remember to **stop your codespace** at `github.com/codespaces` when you finish
for the day; the free allowance is measured in hours.

Full instructions, including the Windows conda route if you'd rather work
offline, are in the *Before you start* section at the top of Notebook 00.

---

## The notebooks

| Notebook | Climate knowledge you will learn | Python skill you will learn | Headline figure |
|---|---|---|---|
| `00_observed_rainfall.ipynb` | GPCP satellite rainfall, 1979–2025. netCDF anatomy, seasonal climatology, the ITCZ, precipitation centroid and hemispheric asymmetry index, the eastern-vs-western Pacific contrast | reading netCDF with `xarray`, `groupby`, area weighting, `pcolormesh` maps, coastlines, **animation**, Hovmöller | the 12-frame animation of the rainband migrating |
| `01_energy_balance.ipynb` | Planetary energy balance, greenhouse effect, ice–albedo feedback, multiple equilibria, Snowball Earth, hysteresis | variables, functions, arrays, loops, root finding, forward Euler | the hysteresis loop |
| `02_insolation.ipynb` | Orbital geometry, declination, day length, daily-mean insolation, the 5.5 PW poleward heat transport, obliquity and Milankovitch | 2-D arrays, `meshgrid`, `contourf`, custom colour maps | the latitude–day insolation map |
| `03_itcz_energy_balance.ipynb` | Moist static energy, a diffusive moist EBM, the energy flux equator, the Bischoff–Schneider ITCZ-shift relation, a Southern Ocean cloud bias pulling the ITCZ south | numerical grids, finite differences, flux-conservative schemes, running an ensemble | ITCZ latitude vs cross-equatorial energy transport, against theory |

Notebook 00 has **five written-answer boxes**. Question 5 asks her to write down
and *date* a guess about why the ITCZ prefers the north, to be reopened at the
end of the project.

Notebooks 01–03 need only `numpy`, `scipy` and `matplotlib` and no data files, so
they run anywhere. Notebook 00 additionally needs `xarray`, `netCDF4` and
`pillow`, all of which the Codespace and `environment.yml` provide.

### The observational numbers she derives in Notebook 00

These are the targets every model in the later notebooks gets scored against:

| sector | centroid | asymmetry index | peak |
|---|---|---|---|
| East Pacific (160°W–80°W) | **+5.15°N** | **+0.569** | 8.0 mm/day at 8.8°N |
| West Pacific (150°E–160°W) | −2.11°N | −0.108 | 8.4 mm/day at 6.2°N |
| Africa / Indian (40–120°E) | +0.16°N | −0.041 | 5.9 mm/day at 3.8°S |
| Global | +0.75°N | +0.105 | 6.0 mm/day at 6.2°N |

The East/West Pacific split is deliberate. Both are "the Pacific" and they give
opposite answers, because the South Pacific Convergence Zone sits in the western
box. The eastern ITCZ never meaningfully leaves the northern hemisphere
(minimum monthly centroid −0.3° in March); the western centroid reaches −5.4°.
Quoting a number without stating the box is meaningless, and she meets that fact
in week one rather than in peer review.

### Results the theory notebooks get right

- Notebook 02 predicts peak poleward energy transport of **5.5 PW near 37°N**;
  observations say about 5.5 PW near 35°N.
- Notebook 03's control run gives **27°C at the equator, −21°C at the pole,
  5.6 PW at 33°N** from one tuned parameter.
- Notebook 03's ITCZ sensitivity is **3.7° per PW** of cross-equatorial energy
  transport; published estimates cluster near 3°/PW.

They also get things wrong in instructive ways, and say so — the energetic
framework predicts an ITCZ near 1°N against the ~5°N she measures herself.

---

## Repository contents

```
00_observed_rainfall.ipynb        start here
01_energy_balance.ipynb
02_insolation.ipynb
03_itcz_energy_balance.ipynb
.devcontainer/devcontainer.json   builds the Codespace automatically
requirements.txt                  packages for the Codespace (pip)
environment.yml                   packages for local Windows/macOS (conda)
data/precip.mon.mean.nc           GPCP v2.3, 20 MB
data/ne_110m_coastline.geojson    Natural Earth coastlines
```

Both data files may sit either in `data/` or beside the notebooks at the top
level — Notebook 00's `fetch()` checks both before downloading anything.

All four notebooks ship with their figures already embedded, so they can be read
before being run.

**No cartopy anywhere.** Coastlines are drawn from the GeoJSON with plain
matplotlib in about twenty readable lines. Cartopy is a notorious install failure
for beginners and buys nothing at this stage.

---

## Setting up the repository (advisor)

The Codespaces route needs these files in a GitHub repo. From this folder:

```bash
git init
git add .
git commit -m "ITCZ notebooks for undergraduate project"
gh repo create fsu-itcz-project --private --source=. --push
```

(or create the repo through the GitHub web UI and push to it). Then add Veronica
as a collaborator: **Settings → Collaborators → Add people**.

---

## Notes on pedagogy

The notebooks are written to be **read**, so try your best to understand the equations and texts attached to each notebook. 


### On AI assistants

Our group welcome any RESPONSIBLE use of AI assistants. In your VS Code, consider leaving **chat** enabled. When you see an error you don't understand, type "explain this error" in the chat box. Try to understand why your code is not working and how you can write them better the next time. 
