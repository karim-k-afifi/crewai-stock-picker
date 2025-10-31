# crewAI Stock Picker

This project uses [crewAI](https://crewai.com) to create a team of autonomous AI agents that collaborate to find, research, and pick a trending stock from a specified sector.

The crew consists of three agents and a manager:
1.  **Trending Company Finder**: Scans the news for trending companies in the given sector.
2.  **Financial Researcher**: Conducts in-depth research on the market position, future outlook, and investment potential of each trending company.
3.  **Stock Picker**: Analyzes the research and selects the single best company for investment, sending a push notification with the final decision.

## Installation

Ensure you have Python >=3.10 <3.13 installed. This project uses [UV](https://docs.astral.sh/uv/) for fast dependency management.

1.  **Install UV:**
    ```bash
    pip install uv
    ```

2.  **Create a virtual environment and install dependencies:**
    From the root of the project, run:
    ```bash
    crewai install
    ```
    This command uses `uv` to create a `.venv` folder and install all the packages defined in your `pyproject.toml`.

## Configuration

Before you can run the crew, you must set up your environment variables.

Create a file named `.env` in the root of your project and add the following:

```env
# For OpenAI Models
OPENAI_API_KEY="sk-..."

# For Pushover Notifications
PUSHOVER_USER="your-pushover-user-key"
PUSHOVER_TOKEN="your-pushover-api-token"
````

Your `stock_picker` agent requires the Pushover keys to send you the final stock pick.

## Running the Project

To kickstart your crew of AI agents, activate your virtual environment (if not already done) and run:

```bash
crewai run
```

This command will:

1.  Execute the crew's tasks as defined in `src/stock_picker/crew.py`.
2.  The agents will research the **'Technology' sector** (as defined in `main.py`).
3.  You will see the agents' work and tool usage in your console.
4.  Final reports will be saved to the `output/` directory:
      * `output/trending_companies.json`
      * `output/research_report.json`
      * `output/decision.md`
5.  You will receive a push notification with the final stock pick.

## Customizing Your Crew

You can easily modify this project to fit your needs:

  * **Change the Sector:** Modify the `inputs` dictionary in `src/stock_picker/main.py` to research a different sector (e.g., 'Healthcare', 'Energy').
  * **Define Agents:** Modify `src/stock_picker/config/agents.yaml` to change the roles, goals, or backstories of your agents.
  * **Define Tasks:** Modify `src/stock_picker/config/tasks.yaml` to change the tasks, descriptions, or expected outputs.
  * **Add Tools:** Add new tools to the `src/stock_picker/tools/` directory and assign them to your agents in `src/stock_picker/crew.py`.