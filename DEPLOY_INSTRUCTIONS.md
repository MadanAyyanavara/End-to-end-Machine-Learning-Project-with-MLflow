# Deployment Instructions for Vercel

To deploy this application to Vercel, follow these steps:

## Prerequisites

1.  **Vercel Account**: Sign up at [vercel.com](https://vercel.com).
2.  **GitHub Repository**: Ensure this project is pushed to a GitHub repository.

## Option 1: Deploy via GitHub Integration (Recommended)

1.  **Commit and Push Changes**:
    Make sure you commit all recent changes, including `vercel.json`, `requirements.txt`, `app.py`, and the updated `.gitignore`.
    
    ```bash
    git add .
    git commit -m "Prepare for Vercel deployment"
    git push origin main
    ```

    **Important**: The trained model file (`artifacts/model_trainer/model.joblib`) MUST be included in the commit. We have updated `.gitignore` to allow this file.

2.  **Import Project in Vercel**:
    - Go to your Vercel Dashboard.
    - Click "Add New..." -> "Project".
    - Select your GitHub repository.
    - Click "Import".
    - In "Configure Project", the default settings should work because `vercel.json` handles the configuration.
    - Click "Deploy".

## Option 2: Deploy via CLI

If you have the Vercel CLI installed:

1.  Run the deployment command:
    ```bash
    vercel
    ```
2.  Follow the prompts to link the project and deploy.

## Troubleshooting

- **Model Loading Errors**: If you encounter errors loading the model (e.g., version mismatch), it might be due to Python version differences (Local Python 3.14 vs Vercel Python 3.9/3.12). If this happens, try retraining the model in a Python environment closer to Vercel's (e.g., Python 3.9) or verify the `scikit-learn` versions match.
- **Missing Dependencies**: We removed `mlflow` and `matplotlib` to keep the deployment lightweight. If the app fails to start due to missing imports, check the logs in Vercel.

## Configuration Details

- `vercel.json`: Configures the Python runtime and routes.
- `requirements.txt`: Optimized list of dependencies for the prediction app.
- `app.py`: Modified to correctly locate the `src` directory on the server.
