{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "0",
   "metadata": {},
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "markdown",
   "id": "1",
   "metadata": {},
   "source": [
    "Zebranie danych z API sejmowgo\n",
    "Matryca poseł x liczba głosowań"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "2",
   "metadata": {},
   "outputs": [],
   "source": [
    "import requests\n",
    "import pandas as pd\n",
    "import networkx as nx\n",
    "from itertools import combinations \n",
    "import numpy as np"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "3",
   "metadata": {},
   "outputs": [],
   "source": [
    "BASE = 'https://api.sejm.gov.pl/sejm'\n",
    "#obecna kadencja\n",
    "TERM = 10\n",
    "\n",
    "\n",
    "#lista posiedzeń\n",
    "def get_sittings():\n",
    "    r = requests.get(f'{base}/term{TERM}/votings')\n",
    "    return r.json()\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "4",
   "metadata": {},
   "outputs": [],
   "source": [
    "#głosowania z danego posiedzenia\n",
    "def get_votes_from_sitting(sitting_num):\n",
    "    r = requests.get(f\"{BASE}/term{TERM}/votings/{sitting_num}\")\n",
    "    votings = r.json()\n",
    "    \n",
    "    votes = []\n",
    "    for v in votings:\n",
    "        voting_num = v[\"votingNumber\"]\n",
    "        detail = requests.get(\n",
    "            f\"{BASE}/term{TERM}/votings/{sitting_num}/{voting_num}\"\n",
    "        ).json()\n",
    "        \n",
    "        for vote in detail.get(\"votes\", []):\n",
    "            votes.append({\n",
    "                \"posel\": vote[\"MP\"],           \n",
    "                \"nazwisko\": vote[\"lastName\"],\n",
    "                \"klub\": vote[\"club\"],\n",
    "                \"glosowanie_id\": f\"{sitting_num}_{voting_num}\",\n",
    "                \"wynik\": vote[\"vote\"]          \n",
    "            })\n",
    "    return votes"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "5",
   "metadata": {},
   "outputs": [],
   "source": [
    "#test, dane z kilku posiedzeń\n",
    "#posiedzneia ze srodka kadencji, bardziej zrozncowane, faktyczne glosowania podparte interesami i ideologia, a nie tylko administracja\n",
    "all_votes = []\n",
    "for sitting in range(20,35):\n",
    "    print(f'Pobieranie dane z posiedzenia {sitting}')\n",
    "    all_votes.extend(get_votes_from_sitting(sitting))\n",
    "\n",
    "df = pd.DataFrame(all_votes)\n",
    "df.to_csv('glosowania_raw.csv', index=False)"
   ]
  }
 ],
 "metadata": {
  "language_info": {
   "name": "python"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}
