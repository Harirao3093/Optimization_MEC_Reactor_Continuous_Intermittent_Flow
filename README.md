For Continuous flow and Intermittent flow
- Use google collab, Upload (Fluid_Classes/Main/Plotting_functions/solver) files from jordan Two_and_Three_Population_MET_Model (1)
- To access my codes Download ipynb file named Final_results_01_09_2023.ipynb for Continuous and intermittent flow.
- To alter reactor dimensions, you can change the dimensions below, make sure the constant files are uploaded in collab.
Continuous Flow
nx = 300
ny = 300
nz = 1
Lx = 1.05  # length in m
Ly = 1  # length in m
Lz = 1.05  # length in m
hrt = 6  # hrt set in any given time units TC is the conversion to seconds
file_name = 'HRT_{}_ym_26_Three_Population_area_optimisation_side_'.format(int(hrt))  # File name to save output data

hrt *= TC_hour  # The hydraulic retention time converted into seconds
baffle_length = 91 / 100  # This is the fraction of the tank a baffle takes up in x
baffle_pairs = 3  # Number of baffle pairs (RHS+LHS) = 1 pair.


New codes where written for intermittent flow
# Update influent only when the flow is ON
            if flow_switch:
                s.intermediate[0, round(int(1 / 2 * ny * 1 / (2 * baffle_pairs + 1) - in_out_points / 2)):round(
                    int(1 / 2 * ny * 1 / (2 * baffle_pairs + 1) - in_out_points / 2 + 1 + in_out_points))] = s.influent

            z2.update_intermediate(rk, irk, dt)
            s2.update_intermediate(rk, irk, dt)
            if flow_switch:
                s2.intermediate[0, round(int(1 / 2 * ny * 1 / (2 * baffle_pairs + 1) - in_out_points / 2)):round(
                    int(1 / 2 * ny * 1 / (2 * baffle_pairs + 1) - in_out_points / 2 + 1 + in_out_points))] = s2.influent

        if (mox.current + (dt / 6) * mox.ddt2 > m_total).any() or (
                mox.current + rk[irk, 0] * dt * mox.ddt1 > m_total).any():
            # If over estimating rk4 loop is reset with smaller timestep
            irk = 0
            dt *= 0.5
            continue

For faster analysis of DATA collected from,
Upload CSV file from the CSV folder, File name (Hari 17-06-2024/Hari 19-06-2024/Hari 25-06-2024/Hari 26-06-2024/Hari 28-06-2024)
To access my codes Download ipnby file named LabVIEW_Output_Graphs_08_09_2023.ipynb

